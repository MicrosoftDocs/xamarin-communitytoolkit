---
title: ListIsNotNullOrEmptyConverter
author: sthewissen
ms.author: joverslu
description: "The ListIsNotNullOrEmptyConverter allows users to convert a binding list value to a boolean indicating whether or not the binding value is null or an empty list."
---

# ListIsNotNullOrEmptyConverter
The ListIsNotNullOrEmptyConverter is a converter that allows users to convert an incoming binding that implements `IEnumerable` to a `bool` value. This value represents if the incoming binding value is **not** `null` or an empty list.

## Syntax
```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:ListIsNotNullOrEmptyConverter x:Key="ListIsNotNullOrEmptyConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyListValue, Converter={StaticResource ListIsNotNullOrEmptyConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
>  Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [ListIsNotNullOrEmptyConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [ListIsNotNullOrEmptyConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/ListIsNotNullOrEmptyConverter.shared.cs)