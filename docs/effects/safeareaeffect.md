---
title: "Xamarin Community Toolkit SafeAreaEffect"
author: sthewissen
ms.author: joverslu
description: "The SafeAreaEffect allows users to offset elements on-screen based on the current active safe area."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit SafeAreaEffect

The `SafeAreaEffect` is an effect that can be added to any element through an attached property to indicate whether or not that element should take current safe areas into account. This is an area of the screen that is safe for all devices that use iOS 11 and greater. Specifically, it will help to make sure that content isn't clipped by rounded device corners, the home indicator, or the sensor housing on an iPhone X. The effect only targets iOS, meaning that on other platforms it does not do anything.

## Syntax

```xml
<StackLayout VerticalAlignment="Center" SafeAreaEffect.SafeArea="true" HorizontalAlignment="Center" Width="400" Height="400">
  ...
</StackLayout>
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| SafeArea | SafeArea | Indicates which safe areas should be taken into account for this element. |

## Specifying a SafeArea

The `SafeArea` property is of type `SafeArea`. This structure takes up to 4 `boolean` type values indicating which safe areas should be taken into account for the element that this effect is applied to. There are three possibilities when creating a `SafeArea` structure:

- Create a `SafeArea` structure defined by a single uniform value. The single value is applied to the left, top, right, and bottom sides of the element.
- Create a `SafeArea` structure defined by horizontal and vertical values. The horizontal value is symmetrically applied to the left and right sides of the element, with the vertical value being symmetrically applied to the top and bottom sides of the element.
- Create a `SafeArea` structure defined by four distinct values that are applied to the left, top, right, and bottom sides of the element.

## Code-behind support

This effect can be also be used from code-behind.

```csharp
public partial class MainPage : ContentPage
{
    public MainPage()
    {
        InitializeComponent();
        SafeAreaEffect.SetSafeArea(stackLayout, new SafeArea(true));
    }
}
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [SafeAreaEffect sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

- [SafeAreaEffect source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Effects/SafeAreaEffect.shared.cs)
