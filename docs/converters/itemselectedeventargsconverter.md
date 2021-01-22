---
title: "Xamarin Community Toolkit ItemSelectedEventArgsConverter"
author: sthewissen
ms.author: joverslu
description: "The ItemSelectedEventArgsConverter allows users to convert ItemSelectedEventArgs to the item that was selected."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ItemSelectedEventArgsConverter

The ItemSelectedEventArgsConverter is a converter that allows users to extract the `SelectedItem` value from an [SelectedItemChangedEventArgs](/dotnet/api/xamarin.forms.selecteditemchangedeventargs) object. It can subsequently be used in combination with `EventToCommandBehavior`.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:ItemSelectedEventArgsConverter x:Key="ItemSelectedEventArgsConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <ListView ItemsSource="{Binding Items}" HasUnevenRows="True">

        <ListView.Behaviors>
            <xct:EventToCommandBehavior EventName="ItemSelected"
                                              Command="{Binding ItemSelectedCommand}"
                                              EventArgsConverter="{StaticResource ItemSelectedEventArgsConverter}" />
        </ListView.Behaviors>

    </ListView>
</ContentPage>
```

## Sample

[ItemSelectedEventArgsConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/ItemSelectedEventArgsPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [ItemSelectedEventArgsConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/ItemSelectedEventArgsConverter.shared.cs)
