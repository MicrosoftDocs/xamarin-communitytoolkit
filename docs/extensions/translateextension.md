---
title: TranslateExtension
author: sthewissen
ms.author: joverslu
description: "The TranslateExtension allows users to handle multi-language support at runtime."
---

# TranslateExtension
The TranslateExtension allows users to handle multi-language support at runtime. It uses the built-in [LocalizationResourceManager]() helper to retrieve the correct translation resource for the current active [CultureInfo](/dotnet/api/system.globalization.cultureinfo).

## Syntax
```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Extensions;assembly=Xamarin.CommunityToolkit"
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

You can see this in action throughout the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [TranslateExtension source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Extensions/TranslateExtension.shared.cs)