---
title: "Xamarin Community Toolkit DockLayout"
description: "The DockLayout makes it easy to dock content in all four directions (top, bottom, left and right)."
author: jfversluis
ms.author: joverslu
ms.date: 12/09/2020
---

# Xamarin Community Toolkit DockLayout

The DockLayout makes it easy to dock content in all four directions (top, bottom, left and right).

This makes it a great choice in many situations, where you want to divide the screen into specific areas. By default, the last element inside the DockLayout will automatically fill the rest of the space (center), unless this feature is specifically disabled.

The actual dock position on the child elements are set through an attached property.

Inspired by [WPF DockPanel](xref:System.Windows.Controls.DockPanel).

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

     <StackLayout>

        <xct:DockLayout
          LastChildFill="False">
          <Button xct:DockLayout.Dock="Top" Text="Top" HeightRequest="50"/>
          <Button xct:DockLayout.Dock="Bottom" Text="Bottom" HeightRequest="50"/>
          <Button xct:DockLayout.Dock="Left" Text="Left" WidthRequest="60"/>
          <Button xct:DockLayout.Dock="Left" Text="Left" WidthRequest="60"/>
          <Button xct:DockLayout.Dock="Right" Text="Right" WidthRequest="80"/>
          <Button xct:DockLayout.Dock="Right" Text="Right" WidthRequest="80"/>
      </xct:DockLayout>

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Dock | Dock | This should be set on the child elements of the `DockLayout`. This determines in what direction the child element is docked. This is a bindable property.  |
| LastChildFill | bool | Gets or sets whether or not the last child defined in the `DockLayout` should fill the remaining space in the center. This is a bindable property. |

## Sample

[DockLayout sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Views/DockLayoutPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [DockLayout source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/DockLayout/DockLayout.shared.cs)
