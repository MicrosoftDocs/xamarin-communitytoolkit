---
title: "Xamarin Community Toolkit EnumToIntConverter"
author: Hottemax
ms.author: joverslu
description: "The EnumToIntConverter is a converter that allows users to convert a standard enum (extending int) to its underlying primitive int type."
ms.date: 05/20/2021
---

# Xamarin Community Toolkit EnumToIntConverter

The EnumToIntConverter is a converter that allows you to convert a standard `Enum` (extending `int`) to its underlying primitive `int` type.
It is useful when binding a collection of values representing an enumeration type with default numbering to a control such as a [Picker](https://docs.microsoft.com/en-us/dotnet/api/xamarin.forms.picker).
For localization purposes or due to other requirements, the enum values often need to be converted to a human-readable string.
In this case, when the user selects a value, the resulting [SelectedIndex](https://docs.microsoft.com/en-us/dotnet/api/xamarin.forms.picker.selectedindex) 
can easily be converted to the underlying `enum` value without requiring additional work in the associated Viewmodel.

## Syntax

```xaml
<?xml version="1.0" encoding="UTF-8" ?>
<ContentPage
  x:Class="Xamarin.CommunityToolkit.Sample.Pages.Converters.EnumToIntConverterPage"
  xmlns="http://xamarin.com/schemas/2014/forms"
  xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
  xmlns:vm="clr-namespace:Xamarin.CommunityToolkit.Sample.ViewModels.Converters"
  xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit">
  <ContentPage.BindingContext>
    <vm:EnumToIntConverterViewModel />
  </ContentPage.BindingContext>
  <ContentPage.Content>
    <StackLayout Padding="10,10" Spacing="10">
      <Picker ItemsSource="{Binding AllStates}" SelectedIndex="{Binding SelectedState, Converter={xct:EnumToIntConverter}}" />
      <Label Text="{Binding Path=SelectedState, Converter={xct:EnumToIntConverter}}" />
    </StackLayout>
  </ContentPage.Content>
</ContentPage>
```

## Sample

[EnumToIntConverter sample page source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/EnumToIntConverterPage.xaml)
[EnumToIntConverter sample viewmodel source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/ViewModels/Converters/EnumToIntConverterViewModel.cs)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [EnumToIntConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/EnumToIntConverter.shared.cs)
