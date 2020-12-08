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
| LowerThumbBorderColor | Color | Gets or sets the border color of the lower thumb for the RangeSlider. This is a bindable property. |
| LowerThumbColor | Color | Gets or sets the color of the lower thumb for the RangeSlider. This is a bindable property. |
| LowerThumbRadius | double | Gets or sets the corner radius of the lower thumb for the RangeSlider. This is a bindable property. |
| LowerThumbSize | double | Gets or sets the size of the lower thumb for the RangeSlider. This is a bindable property. |
| LowerThumbView | View | Gets or sets a custom view to be used for the lower thumb of the RangeSlider. This is a bindable property. |
| LowerValue | double | Gets or sets the lower value of the range for the RangeSlider. This is a bindable property. |
| LowerValueLabelStyle | Style | Gets or sets the style used for the value label on the lower thumb for the RangeSlider. This is a bindable property. |
| MaximumValue | double | Gets or sets the maximum value for the range that can be selected with the RangeSlider. This is a bindable property. |
| MinimumValue | double | Gets or sets the minimum value for the range that can be selected with the RangeSlider. This is a bindable property. |
| StepValue | double | Gets or sets the increment by which MaximumValue and MinimumValue change for the RangeSlider. |
| ThumbBorderColor | Color | Gets or sets the border color of both the lower and the upper thumb for the RangeSlider. This is a bindable property. |
| ThumbColor | Color | Gets or sets the color for both the lower and the upper thumb for the RangeSlider. This is a bindable property. |
| ThumbSize | double | Gets or sets size for both the lower and the upper thumb for the RangeSlider. This is a bindable property. |
| TrackBorderColor | Color | Gets or sets the color of the track bar border for the RangeSlider. This is a bindable property. |
| TrackColor | Color | Gets or sets the color of the track bar for the RangeSlider. This is a bindable property. |
| TrackHighlightBorderColor | Color | Gets or sets the border highlight color of the track bar, which is the part between the lower and the upper thumb, for the RangeSlider. This is a bindable property. |
| TrackHighlightColor | Color | Gets or sets highlight color of the track, which is the part between the lower and the upper thumb, for the RangeSlider. This is a bindable property. |
| TrackRadius | double | Gets or sets the corner radius of the track for the RangeSlider. This is a bindable property. |
| TrackSize | double | Gets or sets the size of the track bar for the RangeSlider. This is a bindable property. |
| UpperThumbBorderColor | Color | Gets or sets the border color of the upper thumb for the RangeSlider. This is a bindable property. |
| UpperThumbColor | Color | Gets or sets the color of the upper thumb for the RangeSlider. This is a bindable property. |
| UpperThumbRadius | double | Gets or sets the corner radius of the upper thumb for the RangeSlider. This is a bindable property. |
| UpperThumbSize | double | Gets or sets the size of the upper thumb for the RangeSlider. This is a bindable property. |
| UpperThumbView | View | Gets or sets a custom view to be used for the upper thumb of the RangeSlider. This is a bindable property. |
| UpperValue | double | Gets or sets the upper value of the range for the RangeSlider. This is a bindable property. |
| UpperValueLabelStyle | Style | Gets or sets the style used for the value label on the upper thumb for the RangeSlider. This is a bindable property. |
| ValueLabelStringFormat | double | Gets or sets the string format used for both the value labels on the lower and upper thumb for the RangeSlider. This is a bindable property. |
| ValueLabelSpacing | double | Gets or sets he spacing of the font used for both the value labels on the lower and upper thumb for the RangeSlider. This is a bindable property. |
| ValueLabelStyle | Style | Gets or sets the style used for both the value labels on the lower and upper thumb of the RangeSlider. This is a bindable property. |

## Events

|Property  |Type  |Description  |
|---------|---------|---------|
| ValueChanged | EventHandler | Occurs when the value changes. |
| LowerValueChanged | EventHandler | Occurs when the lower value of the range changes. |
| UpperValueChanged | EventHandler | Occurs when the upper value of the range changes. |
| DragStarted | EventHandler | Occurs when a drag action is started on the lower or upper thumb. |
| LowerDragStarted | EventHandler | Occurs when a drag action is started with the lower thumb. |
| UpperDragStarted | EventHandler | Occurs when a drag action is started with the upper thumb. |
| DragCompleted | EventHandler | Occurs when a drag action is completed on the lower or upper thumb. |
| LowerDragCompleted | EventHandler | Occurs when a drag action is completed on the lower thumb. |
| UpperDragCompleted | EventHandler | occurs when a drag action is completed on the upper thumb. |

## Sample

[RangeSlider sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Views/RangeSliderPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [RangeSlider source code](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/RangeSlider)
