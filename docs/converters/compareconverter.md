---
title: "Xamarin Community Toolkit CompareConverter"
author: Cfun1
ms.author: joverslu
description: "The CompareConverter allows users to convert a boolean into a specific object."
ms.date: 05/04/2021
---

# Xamarin Community Toolkit CompareConverter

The `CompareConverter` is a converter that converts an object of a type implementing `IComparable`, and returns the comparison
`[value] [ComparisonOperator] [ComparingValue]` result as a boolean if no objects were specified through the `TrueObject` and/or `FalseObject` properties. If values are assigned to the `TrueObject` and/or `FalseObject` properties the `CompareConverter` returns the respective object assigned.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>    
            <x:Double x:Key="ComparingValue">2</x:Double>
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>
        <Slider x:Name="slider" HorizontalOptions="FillAndExpand" Maximum="4"/>
        <Label Text="{Binding Source={x:Reference slider}, Path=Value}"/>
        <Label BackgroundColor="{Binding Source={x:Reference slider}, Path=Value,
                                Converter={xct:CompareConverter ComparisonOperator=Greater,
                                          ComparingValue={StaticResource ComparingValue},
                                          FalseObject=Red, TrueObject=Green}}"
                   Text="{Binding Source={x:Reference slider}, Path=Value,
                            Converter={xct:CompareConverter ComparisonOperator=Greater,
                                    ComparingValue={StaticResource ComparingValue}}}"/>
    </StackLayout>
</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| TrueObject | object | The object that will be returned when the binding value is `true`. |
| FalseObject | object | The object that will be returned when the binding value is `false`. |
| ComparisonOperator | OperatorType | The comparison operator. |
| ComparingValue | IComparable | The object that the bound `value` will be compared to. |

## OperatorType
The `OperatorType` enumeration defines the following members:
- Greater
- GreaterOrEqual
- Equal
- SmallerOrEqual
- Smaller
- NotEqual

## Sample

> [!NOTE]
You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/CompareConverterPage.xaml).

## API

* [CompareConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/CompareConverter.shared.cs)
