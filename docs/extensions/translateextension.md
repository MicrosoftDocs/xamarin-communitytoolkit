---
title: "Xamarin Community Toolkit TranslateExtension"
author: sthewissen
ms.author: joverslu
description: "The TranslateExtension allows users to handle multi-language support at runtime."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit TranslateExtension

The TranslateExtension allows users to handle multi-language support at runtime. It uses the built-in [LocalizationResourceManager](../helpers/localizationresourcemanager.md) helper to retrieve the correct translation resource for the current active [CultureInfo](xref:System.Globalization.CultureInfo).

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

    <StackLayout>

        <Label Text="{xct:Translate AppResources.ATranslatedMessage}" />

        <Label Text="{xct:Translate AppResources.AnotherTranslatedMessage, StringFormat='#{0}'}" />

    </StackLayout>
</ContentPage>
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| StringFormat | string | Allows the user to provide additional formatting to the translated text. |
| Text | string | The resource that will be translated. |

## Sample

[Settings sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/SettingPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [TranslateExtension source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Extensions/TranslateExtension.shared.cs)
