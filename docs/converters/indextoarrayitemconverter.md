---
title: "Xamarin Community Toolkit IndexToArrayItemConverter"
author: sthewissen
ms.author: joverslu
description: "The IndexToArrayItemConverter allows users to retrieve an item from an array based on the binding of an indexer."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit IndexToArrayItemConverter

The IndexToArrayItemConverter is a converter that allows users to convert a `int` value binding to an item in an array. The `int` value being data bound represents the indexer used to access the array. The array is passed in through the `ConverterParameter`.

## Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:IndexToArrayItemConverter x:Key="IndexToArrayItemConverter" />
            <x:Array x:Key="MyArray" Type="x:String">
                <x:String>Value 1</x:String>
                <x:String>Value 2</x:String>
                <x:String>Value 3</x:String>
                <x:String>Value 4</x:String>
                <x:String>Value 5</x:String>
            </x:Array>
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyIntegerValue, Converter={StaticResource IndexToArrayItemConverter}, ConverterParameter={StaticResource MyArray}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [IndexToArrayItemConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [IndexToArrayItemConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/IndexToArrayItemConverter.shared.cs)
