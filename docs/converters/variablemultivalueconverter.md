---
title: "Xamarin Community Toolkit VariableMultiValueConverter"
author: sthewissen
ms.author: joverslu
description: "The VariableMultiValueConverter enables users to check whether or not multiple boolean binding values are true."
ms.date: 12/03/2020
---

# Xamarin Community Toolkit VariableMultiValueConverter

The VariableMultiValueConverter is a converter that allows users to convert multiple `boolean` value bindings to a single `boolean`. It does this by enabling them to specify whether `All`, `Any`, `None` or a specific number of values are `true`. This is useful when combined with the [MultiBinding](/xamarin/xamarin-forms/app-fundamentals/data-binding/multibinding) introduced in Xamarin.Forms.

## Syntax

```xml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="Xamarin.XamarinCommunityToolkit.MultiBindingConverterPage"
             Title="VariableMultiValueConverter">

    <ContentPage.Resources>
        <xct:VariableMultiValueConverter x:Key="AllTrueConverter" ConditionType="All" />
        <xct:VariableMultiValueConverter x:Key="AnyTrueConverter" ConditionType="Any" />
        <xct:VariableMultiValueConverter x:Key="TwoTrueConverter" ConditionType="Exact" Count="2" />
        <xct:InvertedBoolConverter x:Key="InvertedBoolConverter" />
    </ContentPage.Resources>

    <CheckBox>
        <CheckBox.IsChecked>
            <MultiBinding Converter="{StaticResource AllTrueConverter}">
                <Binding Path="Employee.IsOver16" />
                <Binding Path="Employee.HasPassedTest" />
                <Binding Path="Employee.IsSuspended"
                         Converter="{StaticResource InvertedBoolConverter}" />
            </MultiBinding>
        </CheckBox.IsChecked>
    </CheckBox>
</ContentPage>  
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| ConditionType | MultiBindingCondition | Indicates how many values should be true out of the provided boolean values in the MultiBinding. Supports the following values: `All`, `None`, `Any`, `GreaterThan`, `LessThan`. |
| Count | int | The number of values that should be true when using ConditionType `GreaterThan`, `LessThan` or `Exact`. |

## Sample

[VariableMultiValueConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/VariableMultiValueConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [VariableMultiValueConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/VariableMultiValueConverter.shared.cs)
