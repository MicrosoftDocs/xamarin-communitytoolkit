---
title: "Xamarin Community Toolkit NotEqualConverter"
author: sthewissen
ms.author: joverslu
description: "The NotEqualConverter allows users to check whether or not a binding value does not equal another value."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit NotEqualConverter

The NotEqualConverter is a converter that allows users to convert any value binding to a `boolean` depending on whether or not it is equal to a different value. The initial binding contains the object that will be compared and the `ConverterParameter` contains the object to compare it to.

## Syntax

```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:NotEqualConverter x:Key="NotEqualConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyFirstObject, Converter={StaticResource NotEqualConverter}, ConverterParameter=100}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [NotEqualConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [NotEqualConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/NotEqualConverter.shared.cs)
