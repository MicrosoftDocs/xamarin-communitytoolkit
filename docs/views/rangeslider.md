---
title: "Xamarin Community Toolkit RangeSlider"
description: "The RangeSlider control enables the user to select a range of values through a slider."
author: jfversluis
ms.author: joverslu
ms.date: 12/07/2020
---

# Xamarin Community Toolkit RangeSlider

The RangeSlider control enables the user to select a range of values through a slider bar interface. As opposed to a regular [`Slider`](xref:Xamarin.Forms.Slider) that lets you select a single value by sliding the thumb, this control has two thumbs that allows the user to specify a range.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

     <StackLayout>

        <xct:RangeSlider
                x:Name="RangeSlider"
                MaximumValue="10"
                MinimumValue="-10"
                StepValue="1"
                LowerValue="-10"
                UpperValue="10" />

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| MinimumValue | double | Gets or sets which camera device should be used for the CameraView. |
| MaximumValue | double | Gets or sets which camera device should be used for the CameraView. |
| StepValue | double | Gets or sets which camera device should be used for the CameraView. |
| LowerValue | double | Gets or sets which camera device should be used for the CameraView. |
| UpperValue | double | Gets or sets which camera device should be used for the CameraView. |
| ThumbSize | double | Gets or sets which camera device should be used for the CameraView. |
| LowerThumbSize | double | Gets or sets which camera device should be used for the CameraView. |
| UpperThumbSize | double | Gets or sets which camera device should be used for the CameraView. |
| TrackSize | double | Gets or sets which camera device should be used for the CameraView. |
| ThumbColor | Color | Gets or sets which camera device should be used for the CameraView. |
| LowerThumbColor | Color | Gets or sets which camera device should be used for the CameraView. |
| UpperThumbColor | Color | Gets or sets which camera device should be used for the CameraView. |
| TrackColor | Color | Gets or sets which camera device should be used for the CameraView. |
| TrackHighlightColor | Color | Gets or sets which camera device should be used for the CameraView. |
| ThumbBorderColor | Color | Gets or sets which camera device should be used for the CameraView. |
| LowerThumbBorderColor | Color | Gets or sets which camera device should be used for the CameraView. |
| UpperThumbBorderColor | Color | Gets or sets which camera device should be used for the CameraView. |
| TrackBorderColor | Color | Gets or sets which camera device should be used for the CameraView. |
| TrackHighlightBorderColor | Color | Gets or sets which camera device should be used for the CameraView. |
| ValueLabelStyle | Style | Gets or sets which camera device should be used for the CameraView. |
| LowerValueLabelStyle | Style | Gets or sets which camera device should be used for the CameraView. |
| UpperValueLabelStyle | Style | Gets or sets which camera device should be used for the CameraView. |
| ValueLabelStringFormat | double | Gets or sets which camera device should be used for the CameraView. |
| LowerThumbView | View | Gets or sets which camera device should be used for the CameraView. |
| UpperThumbView | View | Gets or sets which camera device should be used for the CameraView. |
| ValueLabelSpacing | double | Gets or sets which camera device should be used for the CameraView. |
| LowerThumbRadius | double | Gets or sets which camera device should be used for the CameraView. |
| UpperThumbRadius | double | Gets or sets which camera device should be used for the CameraView. |
| TrackRadius | double | Gets or sets which camera device should be used for the CameraView. |

## Events

|Property  |Type  |Description  |
|---------|---------|---------|
| ValueChanged | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| LowerValueChanged | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| UpperValueChanged | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| DragStarted | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| LowerDragStarted | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| UpperDragStarted | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| DragCompleted | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| LowerDragCompleted | EventHandler | Gets or sets which camera device should be used for the CameraView. |
| UpperDragCompleted | EventHandler | Gets or sets which camera device should be used for the CameraView. |

## Sample

[RangeSlider sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Views/RangeSliderPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [RangeSlider source code](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/RangeSlider)
