---
title: "Xamarin Community Toolkit LifecycleEffect"
description: "This article explains how to use the LifecycleEffect, to determine when a VisualElement is loaded and unloaded from memory."
author: pedro
ms.author: joverslu
ms.date: 03/11/2021
---

# Xamarin Community Toolkit Lifecycle Effect

The `LifecycleEffect` allows you to determine when a `VisualElement` has its renderer allocated by the platform.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage"
             xmlns:local="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages.Views.TabView">

    <pages:BasePage
    x:Class="Xamarin.CommunityToolkit.Sample.Pages.Effects.LifeCycleEffectPage"
    xmlns="http://xamarin.com/schemas/2014/forms"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:pages="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages"
    xmlns:xct="http://xamarin.com/schemas/2020/toolkit">
    <ContentPage.Content>
        <StackLayout x:Name="stack">
            <StackLayout.Effects>
                <xct:LifecycleEffect Loaded="LifeCycleEffect_Loaded" Unloaded="LifeCycleEffect_Unloaded" />
            </StackLayout.Effects>
            <Label
                HorizontalOptions="CenterAndExpand"
                Text="When you press the button, the Image will appear and after 3 seconds will be removed!"
                VerticalOptions="CenterAndExpand">
                <Label.Effects>
                    <xct:LifecycleEffect Loaded="LifeCycleEffect_Loaded" Unloaded="LifeCycleEffect_Unloaded" />
                </Label.Effects>
            </Label>
            <Image
                x:Name="img"
                IsVisible="false"
                Source="https://raw.githubusercontent.com/xamarin/XamarinCommunityToolkit/main/assets/XamarinCommunityToolkit_128x128.png">
                <Image.Effects>
                    <xct:LifecycleEffect Loaded="LifeCycleEffect_Loaded" Unloaded="LifeCycleEffect_Unloaded" />
                </Image.Effects>
            </Image>
        </StackLayout>
    </ContentPage.Content>

</ContentPage>
```

The `LifeCycleEffect` event handlers are shown below:

```csharp
        void LifeCycleEffect_Loaded(object? sender, EventArgs e)
        {
            if (sender is Button)
                Console.WriteLine("Button loaded");
            if (sender is Image)
                Console.WriteLine("Image loaded");
            if (sender is Label)
                Console.WriteLine("Label loaded");
            if (sender is StackLayout)
                Console.WriteLine("StackLayout loaded");
        }

	void LifeCycleEffect_Unloaded(object? sender, EventArgs e)
	{
		if (sender is Button)
			Console.WriteLine("Button unloaded");
		if (sender is Image)
			Console.WriteLine("Image unloaded");
		if (sender is Label)
			Console.WriteLine("Label unloaded");
		if (sender is StackLayout)
			Console.WriteLine("StackLayout unloaded");
	}
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Loaded | event| Triggers when the renderer for the `VisualElement` is allocated.|
| Unloaded | event| Triggers when the renderer for the `VisualElement` is unallocated. |

## Sample

[LifecycleEffect sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/samples/XCT.Sample/Pages/Effects/LifeCycleEffectPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## Related video

> [!Video https://channel9.msdn.com/Shows/XamarinShow/Lifecycle-Events-Xamarin-Community-Toolkit/player]