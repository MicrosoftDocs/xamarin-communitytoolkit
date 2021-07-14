---
title: "Xamarin Community Toolkit IsInRangeConverter"
author: guoldev
ms.author: joverslu
description: "The IsInRangeConverter allows users to convert a value to a boolean value, checking if the value is between minValue and maxValue."
ms.date: 6/12/2021
---

# Xamarin Community Toolkit IsInRangeConverter

The `IsInRangeConverter` is a converter that allows users to convert a `object` value into a `boolean` value, checking if the value is between `MinValue` and `MaxValue`, returning `true` if the value is within the range and `false` if the value is out of the range.

## Syntax

```
<?xml version="1.0" encoding="UTF-8" ?>
<pages:BasePage
    x:Class="Xamarin.CommunityToolkit.Sample.Pages.Converters.IsInRangeConverterPage"
    xmlns="http://xamarin.com/schemas/2014/forms"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:pages="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages"
    xmlns:vm="clr-namespace:Xamarin.CommunityToolkit.Sample.ViewModels.Converters"
    xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
    x:Name="this">
    <ContentPage.BindingContext>
        <vm:IsInRangeConverterViewModel />
    </ContentPage.BindingContext>
    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:IsInRangeConverter
                x:Key="IsInRangeConverter"
                MaxValue="{Binding Source={x:Reference this}, Path=BindingContext.EndDate}"
                MinValue="{Binding Source={x:Reference this}, Path=BindingContext.StartDate}" />
        </ResourceDictionary>
    </ContentPage.Resources>
    <ContentPage.Content>
        <ScrollView>
            <Grid
                Padding="10"
                ColumnDefinitions="*,*"
                RowDefinitions="Auto,Auto,Auto,Auto,*">
                <Label
                    Grid.Row="0"
                    Grid.Column="0"
                    FontAttributes="Bold"
                    Text="Is Date in range?" />
                <Label
                    Grid.Row="0"
                    Grid.Column="1"
                    FontAttributes="Bold"
                    Text="{Binding Date, Converter={StaticResource IsInRangeConverter}}" />
                <Label
                    Grid.Row="1"
                    Grid.Column="0"
                    Text="Date:" />
                <DatePicker
                    Grid.Row="1"
                    Grid.Column="1"
                    Date="{Binding Date}">
                    <DatePicker.Format>dd/MM/yyyy</DatePicker.Format>
                </DatePicker>
                <Label
                    Grid.Row="2"
                    Grid.Column="0"
                    Text="Start Date:" />
                <DatePicker
                    Grid.Row="2"
                    Grid.Column="1"
                    Date="{Binding StartDate}">
                    <DatePicker.Format>dd/MM/yyyy</DatePicker.Format>
                </DatePicker>
                <Label
                    Grid.Row="3"
                    Grid.Column="0"
                    Text="End Date:" />
                <DatePicker
                    Grid.Row="3"
                    Grid.Column="1"
                    Date="{Binding EndDate}">
                    <DatePicker.Format>dd/MM/yyyy</DatePicker.Format>
                </DatePicker>
            </Grid>
        </ScrollView>
    </ContentPage.Content>
</pages:BasePage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| MinValue | object | The minimum value of the range. |
| MaxValue | object | The maximum value of the range. |

## Sample Project

[IsInRangeConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/IsInRangeConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [IsInRangeConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/IsInRangeConverter.shared.cs)
