---
title: "Xamarin Community Toolkit EqualConverter"
author: sthewissen
ms.author: joverslu
description: "The EqualConverter allows users to check whether or not a binding value equals another value."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit EqualConverter

The EqualConverter is a converter that allows users to convert any value binding to a `bool` depending on whether or not it is equal to a different value. The initial binding contains the object that will be compared and the `ConverterParameter` contains the object to compare it to.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:EqualConverter x:Key="EqualConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyFirstObject, Converter={StaticResource EqualConverter}, ConverterParameter=100}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [EqualConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [EqualConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/EqualConverter.shared.cs)
