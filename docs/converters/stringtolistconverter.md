---
title: "Xamarin Community Toolkit StringToListConverter"
author: guoldev
ms.author: joverslu
description: "The StringToListConverter allows the users to convert a string value into a string array that contains the substrings in the string that are delimited by one or more separators."
ms.date: 01/04/2021
---

# Xamarin Community Toolkit StringToListConverter

![Pre-release API](~/images/pre-release.png)

The `StringToListConverter` is a converter that allows the users to convert a `string` value into a string array that contains the substrings in this string that are delimited by the `Separator`, `Separators`, or `ConverterParameter` property.

## Syntax

```xaml
<?xml version="1.0" encoding="UTF-8" ?>
<pages:BasePage
    x:Class="Xamarin.CommunityToolkit.Sample.Pages.Converters.StringToListConverterPage"
    xmlns="http://xamarin.com/schemas/2014/forms"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:pages="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages"
    xmlns:xct="http://xamarin.com/schemas/2020/toolkit">
    <pages:BasePage.Resources>
        <ResourceDictionary>
            <xct:StringToListConverter x:Key="StringToListConverter" SplitOptions="RemoveEmptyEntries">
                <xct:StringToListConverter.Separators>
                    <x:String>,</x:String>
                    <x:String>.</x:String>
                    <x:String>;</x:String>
                </xct:StringToListConverter.Separators>
            </xct:StringToListConverter>
        </ResourceDictionary>
    </pages:BasePage.Resources>
    <pages:BasePage.Content>
        <Grid Margin="20,0" RowDefinitions="Auto,Auto,*">
            <Label
                Grid.Row="0"
                FontAttributes="Bold"
                Text="Enter some text separated by ',' or '.' or ';'" />
            <Entry
                x:Name="ExampleText"
                Grid.Row="1"
                FontSize="Medium"
                Placeholder="Enter some text separated by ',' or '.' or ';'"
                Text="Item 1,Item 2,Item 3" />
            <ListView
                Grid.Row="2"
                BindingContext="{x:Reference Name=ExampleText}"
                ItemsSource="{Binding Path=Text, Converter={StaticResource StringToListConverter}}">
                <ListView.ItemTemplate>
                    <DataTemplate>
                        <ViewCell>
                            <Label FontSize="Medium" Text="{Binding .}" />
                        </ViewCell>
                    </DataTemplate>
                </ListView.ItemTemplate>
            </ListView>
        </Grid>
    </pages:BasePage.Content>
</pages:BasePage>
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| Separator | string | The string that delimits the substrings in this string. |
| Separators | IList\<string\> | The strings that delimit the substrings in this string. |
| SplitOptions | StringSplitOptions | A bitwise combination of the enumeration values that specifies whether to trim substrings and include empty substrings. |

## Sample project

[StringToListConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/StringToListConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [StringToListConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/StringToListConverter.shared.cs)
