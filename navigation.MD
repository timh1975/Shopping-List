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




