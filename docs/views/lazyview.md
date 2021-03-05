---
title: "Xamarin Community Toolkit LazyView"
description: "This article explains how to use LazyView, which lets you delay the initialization of a View."
author: pedro
ms.author: joverslu
ms.date: 02/11/2021
---

# Xamarin Community Toolkit LazyView

![Pre-release API](~/images/pre-release.png)

The `LazyView` control allows you to delay the initialization of a `View`. You need to provide the type of the `View` that you want to be rendered, using the `x:TypeArguments` XAML namespace attribute, and handle its initialization using the `LoadViewAsync` method. The `IsLoaded` property can be examined to determine when the `LazyView` is loaded.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage"
             xmlns:local="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages.Views.TabView">

     <StackLayout>

        <xct:LazyView x:TypeArguments="local:LazyTestView" IsLoaded = "{Binding IsLoaded}" />

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| IsLoaded | bool| Gets the loaded status of the `LazyView`. |

## Methods

|Property  |Return Type  |Description  |
|---------|---------|---------|
| LoadViewAsync | ValueTask| Initialize the `View`. |
| Dispose | void | Cleans up the `View`, if required. |

## Sample

[LazyView sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/samples/XCT.Sample/Pages/Views/TabView/LazyTabPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).
