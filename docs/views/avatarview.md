---
title: "AvatarView"
description: "The AvatarView control allows the user to display an avatar or the user's initials if no avatar is available."
author: sthewissen
ms.author: joverslu
ms.date: 10/09/2020
---

# AvatarView
The AvatarView control allows the user to display an avatar or the user's initials if no avatar is available. By binding the `Source` property the user can assign an image to the AvatarView. Simultaneously binding the `Text` property will allow the user to also set the initials to be shown if no valid image is provided.

## Syntax
```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="clr-namespace:Xamarin.CommunityToolkit.Converters;assembly=Xamarin.CommunityToolkit"
             x:Class="MyLittleApp.MainPage">

     <StackLayout>

        <xct:AvatarView Text="{Binding Initials}" Source="{Binding AvatarSource}" />

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| BorderColor | [`Color`](xref:Xamarin.Forms.Color)| Gets or sets the border color for the AvatarView. |
| Color | [`Color`](xref:Xamarin.Forms.Color) | Gets or sets the color which will fill the background of a AvatarView. |
| CornerRadius | double | Gets or sets the corner radius of the AvatarView. |
| FontAttributes | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | Gets a value that indicates whether the font for the label is bold, italic, or neither. |
| FontFamily | string | Gets the font family to which the font for the label belongs. |
| FontSize | double | Gets the size of the font for the label. |
| Size | double | Gets or sets the desired height and width of the AvatarView. |
| Source | [`ImageSource`](xref:Xamarin.Forms.ImageSource) | Gets or sets the source of the image. This is a bindable property. |
| Text | string | Gets or sets the text for the label. This is a bindable property. |
| TextColor | [`Color`](xref:Xamarin.Forms.Color)| Gets or sets the Color for the text of the label. This is a bindable property. |

## Sample

[AvatarView sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Views/AvatarViewPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [AvatarView source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Views/AvatarView.shared.cs)