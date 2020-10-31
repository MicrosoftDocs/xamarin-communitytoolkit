---
title: "Xamarin Community Toolkit StringToIntConverter"
author: sthewissen
ms.author: joverslu
description: "The StringToIntConverter allows users to convert an incoming string value to an int."
ms.date: 10/31/2020
---

# Xamarin Community Toolkit StringToIntConverter

The StringToIntConverter is a converter that allows users to convert an incoming `string` value to an `int`.

## Syntax

```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:StringToIntConverter x:Key="StringToIntConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label Text="{Binding MyString, Converter={StaticResource StringToIntConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [StringToIntConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [StringToIntConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/StringToIntConverter.shared.cs)
