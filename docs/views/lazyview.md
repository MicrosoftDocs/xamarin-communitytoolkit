---
title: "Xamarin Community Toolkit LazyView"
description: "This article explains how to use LazyView."
author: pedro
ms.author: joverslu
ms.date: 02/11/2021
---

# Xamarin Community Toolkit LazyView

The LazyView control allows you to delay the initialization of a `View`. You need to provide the type of the `View`, using the `x:TypeArguments` XAML's parameter, that you want to be rendered and handle the initialization using the `LoadViewAsync` method. You can look to the `IsLoaded` property to know when the LazyView is Loaded.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage"
             xmlns:local="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages.Views.TabView">

     <StackLayout>

        <xct:LazyView x:TypeArguments="local:LazyTestView" IsLoaded = "{Binding IsLoaded}"/>

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| IsLoaded | bool| Gets loaded status of the LazyView. |

## Methods

|Property  |Return Type  |Description  |
|---------|---------|---------|
| LoadViewAsync | ValueTask| Initialize the view. |
| Dispose | void | Cleans up the View if needed |

## Sample

[LazyView sample page Source](https://github1s.com/xamarin/XamarinCommunityToolkit/blob/develop/samples/XCT.Sample/Pages/Views/TabView/LazyTabPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).
