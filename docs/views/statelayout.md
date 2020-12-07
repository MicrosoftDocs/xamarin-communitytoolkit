---
title: "Xamarin Community Toolkit StateLayout"
description: "The StateLayout control allows the user to turn any layout element into an individual state-aware element."
author: sthewissen
ms.author: joverslu
ms.date: 10/09/2020
---

# Xamarin Community Toolkit StateLayout

Displaying a specific view when your app is in a specific state is a common pattern throughout any mobile app. Examples range from creating loading views to overlay on the screen, or on a subsection of the screen. Empty state views can be created for when there's no data to display, and error state views can be displayed when an error occurs.

## Getting started

The StateLayout control enables the user to turn any layout element like a `Grid` or `StackLayout` into an individual state-aware element. Each layout that you make state-aware, using the StateLayout attached properties, contains a collection of `StateView` objects. These objects can be used as templates for the different states supported by StateLayout. Whenever the `CurrentState` property is set to a value that matches the `State` property of one of the StateViews its contents will be displayed instead of the main content.

### LayoutState enumeration

The `LayoutState` enumeration supports one of the following values:

- `None` (default, this will show the initial view)
- `Loading`
- `Saving`
- `Success`
- `Error`
- `Empty`
- `Custom`

### Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Views;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

     <Grid xct:StateLayout.CurrentState="{Binding CurrentState}">
      <xct:StateLayout.StateViews>
         <xct:StateView StateKey="Loading">
            <Grid BackgroundColor="White">
               <StackLayout VerticalOptions="Center" HorizontalOptions="Center">
                  <ActivityIndicator Color="#1abc9c" />
                  <Label Text="Loading..." HorizontalOptions="Center" />
               </StackLayout>
            </Grid>
         </xct:StateView>
      </xct:StateLayout.StateViews>      

     ...

  </Grid>

</ContentPage>
```

## Use custom states

Besides the built-in states StateLayout also supports a `Custom` state. By setting `State` to `Custom` and adding a `CustomStateKey` you can create custom states beyond the built-in states. You can use the `CurrentCustomStateKey` on your root StateLayout element to bind a variable that indicates when to show one of your custom states.

### Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Views;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <StackLayout Padding="10" xct:StateLayout.CurrentState="{Binding CurrentState}" xct:StateLayout.CurrentCustomStateKey="{Binding CustomState}">
        <xct:StateLayout.StateViews>
            <xct:StateView StateKey="Custom" CustomStateKey="ThisIsACustomState">
                <Label Text="Hi, I'm a custom state!" />
            </xct:StateView>
            <xct:StateView StateKey="Custom" CustomStateKey="ThisIsACustomStateToo">
                <Label Text="Hi, I'm a custom state too!" />
            </xct:StateView>
        </xct:StateLayout.StateViews>

        <Label Text="This is the normal state." />
    </StackLayout>

</ContentPage>
```

## Use repeating states

When loading multiple items of the same type it could be beneficial to repeat a piece of XAML without having to copy paste it multiple times. This is where the `RepeatCount` property should be used. By defining a `RepeatTemplate` it's possible to repeat the same piece of XAML while only defining it once.

### Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Views;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <StackLayout xct:StateLayout.CurrentState="{Binding CurrentState}">
        <xct:StateLayout.StateViews>
            <xct:StateView StateKey="Loading" RepeatCount="3">
                <xct:StateView.RepeatTemplate>
                    <DataTemplate>
                        <StackLayout Spacing="8">
                            <BoxView CornerRadius="8" HeightRequest="40" BackgroundColor="#CCCCCC" WidthRequest="120" />
                            <BoxView CornerRadius="8" HeightRequest="40" BackgroundColor="#CCCCCC" WidthRequest="200" />
                        </StackLayout>
                    </DataTemplate>
                </xct:StateView.RepeatTemplate>
            </xct:StateView>
        </xct:StateLayout.StateViews>

        ...

    <StackLayout>
</ContentPage>
```

## Properties

The following properties are available on the `StateLayout` object:

|Property  |Type  |Description  |
|---------|---------|---------|
| CurrentState | `LayoutState` | Defines the current state of the layout and which template to show. |
| CurrentCustomStateKey | string | Pair this with `State="Custom"` on a StateView to add custom states. |
| StateViews | `IList<StateView>` | A list of StateView objects that contains a template per State. |

The following properties are available on the `StateView` object:

|Property  |Type  |Description  |
|---------|---------|---------|
| CustomStateKey | string | Defines the current state of the layout and which template to show. |
| RepeatCount | int | Defines the current state of the layout and which template to show. |
| RepeatTemplate | [`DataTemplate`](xref:Xamarin.Forms.DataTemplate)  | Defines the current state of the layout and which template to show. |
| State | `LayoutState` | Defines the current state of the layout and which template to show. |

## Sample

[StateLayout sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Views/StateLayoutPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [StateLayout source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Views/StateLayout/StateLayout.shared.cs)
