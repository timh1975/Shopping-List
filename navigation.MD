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
<ShellContent
    Title="Create Shopping List"
    ContentTemplate="{DataTemplate view:CreateListView}"
    Route="CreateListView" />

```
This line adds CreateListView to the ShellContent



