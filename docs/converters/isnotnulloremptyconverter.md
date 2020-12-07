---
title: "Xamarin Community Toolkit IsNotNullOrEmptyConverter"
author: sthewissen
ms.author: joverslu
description: "The IsNotNullOrEmptyConverter allows users to convert a binding value to a boolean indicating whether or not the binding value is null or empty."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit IsNotNullOrEmptyConverter

The IsNotNullOrEmptyConverter is a converter that allows users to convert an incoming binding to a `bool` value. This value represents if the incoming binding value is **not** `null` or empty.

## Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:IsNotNullOrEmptyConverter x:Key="IsNotNullOrEmptyConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyStringValue, Converter={StaticResource IsNotNullOrEmptyConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [IsNotNullOrEmptyConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [IsNotNullOrEmptyConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/IsNotNullOrEmptyConverter.shared.cs)
