---
title: "Xamarin Community Toolkit TextCaseConverter"
author: sthewissen
ms.author: joverslu
description: "The TextCaseConverter allows users to change the casing of a string value."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit TextCaseConverter

The TextCaseConverter is a converter that allows users to convert the casing of an incoming `string` type binding. The `Type` property is used to define what kind of casing will be applied to the `string`.

## Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:TextCaseConverter x:Key="TextCaseConverter" Type="Upper" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyString, Converter={StaticResource TextCaseConverter}}" />

    </StackLayout>
</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Type | TextCaseType | The type of casing to apply to the `string` value. |

## TextCaseType

The `TextCaseType` enumeration defines the following members:

- `None` - Applies no specific formatting to the string.
- `Upper` - Applies upper case formatting to the string.
- `Lower` - Applies lower case formatting to the string.

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [TextCaseConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

- [TextCaseConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/TextCaseConverter.shared.cs)
- [TextCaseType source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/TextCaseType.shared.cs)
