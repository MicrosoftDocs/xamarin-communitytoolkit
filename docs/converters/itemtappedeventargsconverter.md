---
title: "Xamarin Community Toolkit ItemTappedEventArgsConverter"
author: sthewissen
ms.author: joverslu
description: "The ItemTappedEventArgsConverter allows users to convert ItemTappedEventArgs to the item that was selected."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ItemTappedEventArgsConverter

The ItemTappedEventArgsConverter is a converter that allows users to extract the `Item` value from an [ItemTappedEventArgs](/dotnet/api/xamarin.forms.itemtappedeventargs) object. It can subsequently be used in combination with `EventToCommandBehavior`.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:ItemTappedEventArgsConverter x:Key="ItemTappedEventArgsConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <ListView ItemsSource="{Binding Items}" HasUnevenRows="True">

        <ListView.Behaviors>
            <xct:EventToCommandBehavior EventName="ItemTapped"
                                              Command="{Binding ItemTappedCommand}"
                                              EventArgsConverter="{StaticResource ItemTappedEventArgsConverter}" />
        </ListView.Behaviors>

    </ListView>
</ContentPage>
```

## Sample

[ItemTappedEventArgsConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/ItemTappedEventArgsPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [ItemTappedEventArgsConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/ItemTappedEventArgsConverter.shared.cs)
