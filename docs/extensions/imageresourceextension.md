---
title: "Xamarin Community Toolkit ImageResourceExtension"
author: sthewissen
ms.author: joverslu
description: "The ImageResourceExtension allows users to display an image from an embedded resource."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ImageResourceExtension

The `ImageResourceExtension` is an extension that can be used to display an image from an embedded resource. By providing the resource ID of the embedded resource to this extension, you can bind the embedded resource to the `Source` property of an [Image](/xamarin/xamarin-forms/user-interface/images) control.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Extensions;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

    <StackLayout>

        <Image Source="{xct:ImageResource Id=MyLittleApp.Resources.MyImage}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [ImageResourceExtension sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [ImageResourceExtension source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Extensions/ImageResourceExtension.shared.cs)
