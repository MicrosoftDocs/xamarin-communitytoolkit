---
title: ListToStringConverter
author: sthewissen
ms.author: joverslu
description: "The ListToStringConverter allows users to convert a list of values to a single string value."
---

# ListToStringConverter
The ListToStringConverter is a converter that allows users to convert an incoming binding that implements `IEnumerable` to a single `string` value. The `Separator` property is used to join the items in the `IEnumerable`.

## Syntax
```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:ListToStringConverter x:Key="ListToStringConverter" Separator=", " />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyListValue, Converter={StaticResource ListToStringConverter}}" />

    </StackLayout>
</ContentPage>
```

## Properties
|Property  |Type  |Description  |
|---------|---------|---------|
| Separator | string | The separator that will be used to join the items in the list. |

## Sample

> [!NOTE]
>  Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [ListToStringConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [ListToStringConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/ListToStringConverter.shared.cs)