---
title: "Xamarin Community Toolkit IsNullOrEmptyConverter"
author: sthewissen
ms.author: joverslu
description: "The IsNullOrEmptyConverter allows users to convert a binding value to a boolean indicating whether or not the binding value is null or empty."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit IsNullOrEmptyConverter

The IsNullOrEmptyConverter is a converter that allows users to convert an incoming binding to a `bool` value. This value represents if the incoming binding value is `null` or empty.

## Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:IsNullOrEmptyConverter x:Key="IsNullOrEmptyConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyStringValue, Converter={StaticResource IsNullOrEmptyConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [IsNullOrEmptyConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [IsNullOrEmptyConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/IsNullOrEmptyConverter.shared.cs)
