---
title: "Xamarin Community Toolkit ItemTappedEventArgsConverter"
author: sthewissen
ms.author: joverslu
description: "The ItemTappedEventArgsConverter allows users to convert ItemSelectedEventArgs to the item that was actually selected."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ItemTappedEventArgsConverter

The ItemTappedEventArgsConverter is a converter that allows users to extract the `Item` value from an [ItemTappedEventArgs](/dotnet/api/xamarin.forms.itemtappedeventargs) object. It can subsequently be used in combination with `EventToCommandBehavior`.

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
            <converters:ItemTappedEventArgsConverter x:Key="ItemTappedEventArgsConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <ListView ItemsSource="{Binding Items}" HasUnevenRows="True">

        <ListView.Behaviors>
            <behaviors:EventToCommandBehavior EventName="ItemTapped"
                                              Command="{Binding ItemTappedCommand}"
                                              EventArgsConverter="{StaticResource ItemTappedEventArgsConverter}" />
        </ListView.Behaviors>

    </ListView>
</ContentPage>
```

## Sample

[ItemTappedEventArgsConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/ItemTappedEventArgsPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [ItemTappedEventArgsConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/ItemTappedEventArgsConverter.shared.cs)
