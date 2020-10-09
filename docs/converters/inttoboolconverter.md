---
title: "Xamarin Community Toolkit IntToBoolConverter"
author: sthewissen
ms.author: joverslu
description: "The IntToBoolConverter allows users to convert an incoming integer value to a boolean."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit IntToBoolConverter

The IntToBoolConverter is a converter that allows users to convert an incoming `int` value to a `bool`. If the incoming `int` value is 0, it will be converted to `false`. Any other incoming value will be converted to `true`.

## Syntax

```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:IntToBoolConverter x:Key="IntToBoolConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyIntegerValue, Converter={StaticResource IntToBoolConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [IntToBoolConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [IntToBoolConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/IntToBoolConverter.shared.cs)
