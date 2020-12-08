---
title: "Xamarin Community Toolkit BadgeView"
description: "The BadgeView allows the user to show a badge with a string value on top of any control."
author: jfversluis
ms.author: joverslu
ms.date: 12/08/2020
---

# Xamarin Community Toolkit BadgeView

The `BadgeView` allows the user to show a badge with a string value on top of any control. By wrapping a control in a `BadgeView` control, the user can now show a badge value on top of it. This is very much alike the badges you see on the app icons on iOS and Android.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

     <StackLayout>

        <xct:BadgeView
            BackgroundColor="Red"
            FontAttributes="Bold"
            FontSize="Medium"
            TextColor="White"
            Text="1">
            <Label
                Text="This label has a badge in the top-right"/>
        </xct:BadgeView>

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| AutoHide | bool | Gets or sets if the badge should be hidden automatically when the value is `"0"`. This is a bindable property. |
| BackgroundColor | [`Color`](xref:Xamarin.Forms.Color) | Gets or sets the background color for the badge. This is a bindable property. |
| BadgeAnimation | IBadgeAnimation | Gets or sets the animation that should be used when the badge is shown or hidden. Only works if `IsAnimated` is set to `true`. This is a bindable property. |
| BadgePosition | BadgePosition | Gets or sets the position where the badge will be shown relative to the `Content`. This is a bindable property. |
| BorderColor | [`Color`](xref:Xamarin.Forms.Color) | Gets or sets the border color for the badge. This is a bindable property. |
| Content | [`View`](xref:Xamarin.Forms.View) | Gets or sets the `View` on top of which the `BadgeView` will be shown. This is a bindable property. |
| FontAttributes | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | Gets or sets the font attributes to be used for the text of the `BadgeView`. This is a bindable property. |
| FontFamily | string | Gets or sets the font to be used for the text of the `BadgeView`. This is a bindable property. |
| FontSize | double | Gets or sets the font size for the text of the `BadgeView`. [`NamedSize`](xref:Xamarin.Forms.NamedSize) values can be used. This is a bindable property. |
| HasShadow | bool | Gets or sets if the badge should have a shadow when shown. This is a bindable property. |
| IsAnimated | bool | Gets or sets if the badge should be animated when it is shown or hidden. This is a bindable property. |
| Text | string | Gets or sets the text for the badge. This is a bindable property. |
| TextColor | [`Color`](xref:Xamarin.Forms.Color) | Gets or sets the text color for the badge. This is a bindable property. |

## Sample

[BadgeView sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Views/BadgeViewPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [BadgeView source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/BadgeView/BadgeView.shared.cs)
