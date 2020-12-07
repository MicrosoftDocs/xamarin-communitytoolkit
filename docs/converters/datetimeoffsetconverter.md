---
title: "Xamarin Community Toolkit DateTimeOffsetConverter"
author: sthewissen
ms.author: joverslu
description: "The DateTimeOffsetConverter allows users to convert a DateTimeOffset to a DateTime."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit DateTimeOffsetConverter

The DateTimeOffsetConverter is a converter that allows users to convert a `DateTimeOffset` to a `DateTime`. Sometimes a datetime value is stored with the offset on a backend to allow for storing the timezone in which a `DateTime` originated from. Controls like the `DatePicker` in Xamarin.Forms will only work with `DateTime`. This converter can be used in those scenarios.

## Syntax

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">
    <ContentPage.Resources>
         <ResourceDictionary>
             <xct:DateTimeOffsetConverter x:Key="DateTimeOffsetConverter" />
         </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label Text="{Binding MyDateTimeOffset, Converter={StaticResource DateTimeOffsetConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

[DateTimeOffsetConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/DateTimeOffsetConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [DateTimeOffsetConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/DateTimeOffsetConverter.shared.cs)
