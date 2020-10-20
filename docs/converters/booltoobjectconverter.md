---
title: "Xamarin Community Toolkit BoolToObjectConverter"
author: sthewissen
ms.author: joverslu
description: "The BoolToObjectConverter allows users to convert a boolean into a specific object."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit BoolToObjectConverter

The BoolToObjectConverter is a converter that allows users to convert a `bool` value binding to a specific object. By providing both a `TrueObject` and a `FalseObject` in the converter the appropriate object will be used depending on the value of the binding.

## Syntax

```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
         <ResourceDictionary>
             <xct:BoolToObjectConverter x:Key="BoolToObjectConverter" TrueObject="16" FalseObject="10" />
         </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Label Text="Hi there from the Docs!" FontSize="{Binding MyBoolean, Converter={StaticResource BoolToObjectConverter}}" />

    </StackLayout>
</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| TrueObject | object | The object that will be used when the binding value is `true`. |
| FalseObject | object | The object that will be used when the binding value is `false`. |


## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [BoolToObjectConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [BoolToObjectConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Converters/BoolToObjectConverter.shared.cs)
