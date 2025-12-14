# How to navigate in MAUI using APP SHell

## WHat is App Shell


## How does it differ from PageNavigation


### Register route in App.xaml.cs

``` 

using Microsoft.Extensions.DependencyInjection;
using Shopping_List.Views;

namespace Shopping_List
{
    public partial class App : Application
    {
        public App()
        {
            InitializeComponent();

            Routing.RegisterRoute(nameof(CreateListView), typeof(CreateListView));

        }

        protected override Window CreateWindow(IActivationState? activationState)
        {
            return new Window(new AppShell());
        }
    }
}

```

```
using Shopping_List.Views;
```

The using statement exposes the Views folder to the App class. Teh Views folder will contain the XAML markup file for the UI

```
 Routing.RegisterRoute(nameof(CreateListView), typeof(CreateListView));

```

The Routing.RegisterRoute will register the root to the CreateListView view page

### Add the CreateListView to AppShell.xaml

```
<?xml version="1.0" encoding="UTF-8" ?>
<Shell
    x:Class="Shopping_List.AppShell"
    xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:local="clr-namespace:Shopping_List"
    xmlns:view ="clr-namespace:Shopping_List.Views"
    Title="Shopping_List">

    <ShellContent
        Title="Shopping List"
        ContentTemplate="{DataTemplate local:MainPage}"
        Route="MainPage" />

    <ShellContent
        Title="Create Shopping List"
        ContentTemplate="{DataTemplate view:CreateListView}"
        Route="CreateListView" />


</Shell>


'``
``` 
xmlns:view ="clr-namespace:Shopping_List.Views"

```

xmlns is the namespace for the View folder

```
```
<ShellContent
    Title="Create Shopping List"
    ContentTemplate="{DataTemplate view:CreateListView}"
    Route="CreateListView" />

```
This line adds CreateListView to the ShellContent

### Add the view(s) to the builder services to teh MauiPrograms.cs

```
using Microsoft.Extensions.Logging;
using Shopping_List.ViewModel;

namespace Shopping_List
{
    public static class MauiProgram
    {
        public static MauiApp CreateMauiApp()
        {
            var builder = MauiApp.CreateBuilder();
            builder
                .UseMauiApp<App>()
                .ConfigureFonts(fonts =>
                {
                    fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
                    fonts.AddFont("OpenSans-Semibold.ttf", "OpenSansSemibold");
                });


            builder.Services.AddTransient<MainPage>();
            builder.Services.AddTransient<MainPageViewModel>();


#if DEBUG
            builder.Logging.AddDebug();
#endif

            return builder.Build();
        }
    }
}

```
```
builder.Services.AddTransient<MainPageViewModel>();

```
This adds the ViewModels to the builder services.  The ViewModel will be discussed below

### The ViewModels






