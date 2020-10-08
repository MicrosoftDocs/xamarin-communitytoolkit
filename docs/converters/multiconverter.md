---
title: MultiConverter
author: sthewissen
ms.author: joverslu
description: "The MultiConverter allows users to offset elements on-screen based on the current active safe area."
---

# MultiConverter
The ListToStringConverter is a converter that allows users to chain multiple converters together. The initial binding value is passed through to the first converter and, depending on what these converters return, that value is subsequently passed through to the next converter.

## Syntax
```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <xct:MultiConverter x:Key="MultiConverter">
                <xct:TextCaseConverter />
                <xct:NotEqualConverter />
            </xct:MultiConverter>
            <x:Array x:Key="MultiConverterParams" Type="{x:Type xct:MultiConverterParameter}">
                <xct:MultiConverterParameter ConverterType="{x:Type xct:TextCaseConverter}" Value="{x:Static xct:TextCaseType.Upper}" />
                <xct:MultiConverterParameter ConverterType="{x:Type xct:NotEqualConverter}" Value="ANDREI ROCKS 🎸" />
            </x:Array>
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label IsVisible="{Binding MyStringValue, Converter={StaticResource MultiConverter}, ConverterParameter={StaticResource MultiConverterParams}}" />

    </StackLayout>
</ContentPage>
```

## Working with parameters
Due to the nature of how converters work it is not possible to pass parameters to each individual converter in the MultiConverter. To work around this an `IList` of `MultiConverterParameter` objects is accepted as the converter parameter of the MultiConverter. These objects represent the parameters you want to provide for each individual converter. The MultiConverter subsequently matches the type of one of its converters to the type provided in the `ConverterType` property of a `MultiConverterParameter`. It then takes the provided `Value` property and uses that as the `ConverterParameter` of that specific converter.

## Sample

[MultiConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/MultiConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MultiConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/MultiConverter.shared.cs)