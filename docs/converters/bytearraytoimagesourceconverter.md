---
title: "Xamarin Community Toolkit ByteArrayToImageSourceConverter"
author: sthewissen
ms.author: joverslu
description: "The ByteArrayToImageSourceConverter allows users to show an image based on a byte array."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ByteArrayToImageSourceConverter

The ByteArrayToImageSourceConverter is a converter that allows the user to convert an incoming value from byte array and returns an object of type `ImageSource`. This object can then be used as the `Source` of an `Image` control.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">
    <ContentPage.Resources>
         <ResourceDictionary>
             <xct:ByteArrayToImageSourceConverter x:Key="ByteArrayToImageSourceConverter" />
         </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Image Source="{Binding MyByteArray, Converter={StaticResource ByteArrayToImageSourceConverter}}" />

    </StackLayout>
</ContentPage>
```

## Sample

[ByteArrayToImageSourceConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/ByteArrayToImageSourcePage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [ByteArrayToImageSourceConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/ByteArrayToImageSourceConverter.shared.cs)
