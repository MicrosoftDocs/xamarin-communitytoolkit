---
title: "Xamarin Community Toolkit ListIsNullOrEmptyConverter"
author: sthewissen
ms.author: joverslu
description: "The ListIsNullOrEmptyConverter allows users to convert a binding list value to a boolean indicating whether or not the binding value is null or an empty list."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ListIsNullOrEmptyConverter

The ListIsNullOrEmptyConverter is a converter that allows users to convert an incoming binding that implements `IEnumerable` to a `bool` value. This value represents if the incoming binding value is either `null` or an empty list.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:ListIsNullOrEmptyConverter x:Key="ListIsNullOrEmptyConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyListValue, Converter={StaticResource ListIsNullOrEmptyConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [ListIsNullOrEmptyConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [ListIsNullOrEmptyConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/ListIsNullOrEmptyConverter.shared.cs)
