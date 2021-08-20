---
title: "Xamarin Community Toolkit UtcDateTimeToLocalStringConverter"
author: leojharris
ms.author: joverslu
description: The UtcDateTimeToLocalStringConverter allows users to convert an incoming DateTime or DateTimeOffset value to a local string, using the provided datetime format.
ms.date: 20/08/2021
---

# Xamarin Community Toolkit UtcDateTimeToLocalStringConverter

The UtcDateTimeToLocalStringConverter is a converter that allows users to convert an incoming `DateTime` or `DateTimeOffset` value to a local `string`. An optional date/time pattern can be provided, otherwise the general date/time pattern (short time) will be used.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <x:String x:Key="dateTimeFormat">MM/dd/yyyy h:mm tt</x:String>
            <xct:UtcDateTimeToLocalStringConverter x:Key="UtcDateTimeToLocalStringConverter"  DateTimeFormat="{StaticResource dateTimeFormat}"/>
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label Text="{Binding UtcDateTime, Converter={StaticResource UtcDateTimeToLocalStringConverter}}" />

    </StackLayout>
</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| DateTimeFormat | string | The date/time pattern to be used for the local string. Default is general date/time pattern (short time) |

## Sample

[UtcDateTimeToLocalStringConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/UtcDateTimeToLocalStringConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [UtcDateTimeToLocalStringConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/UtcDateTimeToLocalStringConverter.shared.cs)

