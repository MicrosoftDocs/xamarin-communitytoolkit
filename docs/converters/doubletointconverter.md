---
title: "Xamarin Community Toolkit DoubleToIntConverter"
author: sthewissen
ms.author: joverslu
description: "The DoubleToIntConverter allows users to convert an incoming double value to an int."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit DoubleToIntConverter

The DoubleToIntConverter is a converter that allows users to convert an incoming `double` value to an `int`. Optionally the user can provide a multiplier to the conversion through the `Ratio` property.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:DoubleToIntConverter x:Key="DoubleToIntConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label Text="{Binding MyDouble, Converter={StaticResource DoubleToIntConverter}, ConverterParameter=2}" />

    </StackLayout>
</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Ratio | int | The multiplier to apply to the conversion. |

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [DoubleToIntConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [DoubleToIntConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/DoubleToIntConverter.shared.cs)
