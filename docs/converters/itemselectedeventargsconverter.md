---
title: ItemSelectedEventArgsConverter
author: sthewissen
ms.author: joverslu
description: "The ItemSelectedEventArgsConverter allows users to offset elements on-screen based on the current active safe area."
---

# ItemSelectedEventArgsConverter
The ItemSelectedEventArgsConverter is a converter that allows users to extract the `SelectedItem` value from an [SelectedItemChangedEventArgs](/dotnet/api/xamarin.forms.selecteditemchangedeventargs) object. It can subsequently be used in combination with `EventToCommandBehavior`.

## Syntax
```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:converters="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             xmlns:behaviors="clr-namespace:Xamarin.CommunityToolkit.Behaviors;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <converters:ItemSelectedEventArgsConverter x:Key="ItemSelectedEventArgsConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <ListView ItemsSource="{Binding Items}" HasUnevenRows="True">

        <ListView.Behaviors>
            <behaviors:EventToCommandBehavior EventName="ItemSelected"
                                              Command="{Binding ItemSelectedCommand}"
                                              EventArgsConverter="{StaticResource ItemSelectedEventArgsConverter}" />
        </ListView.Behaviors>

    </ListView>
</ContentPage>
```

## Sample

[ItemSelectedEventArgsConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/ItemSelectedEventArgsPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [ItemSelectedEventArgsConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/ItemSelectedEventArgsConverter.shared.cs)