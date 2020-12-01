---
title: "CameraView"
description: "The CameraView control allows the user to display camera preview, take pictures and record videos."
author: jfversluis
ms.author: joverslu
ms.date: 12/01/2020
---

# CameraView

The CameraView control allows the user to display a preview window of the camera output. In addition, it can take pictures or record videos. The CameraView also offers the options you would expect to support taking photos and recording videos such as: turning the flash on or off, save the captured media to a file and offer different hooks for events.

## Syntax

```xml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

     <StackLayout>

        <xct:CameraView
                x:Name="cameraView"
                CaptureOptions="Video"
                FlashMode="On"
                HorizontalOptions="FillAndExpand"
                MediaCaptured="CameraView_MediaCaptured"
                OnAvailable="CameraView_OnAvailable"
                SavePhotoToFile="True"
                VerticalOptions="FillAndExpand" />

    </StackLayout>

</ContentPage>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| MediaCaptured | EventHandler&lt;MediaCapturedEventArgs&gt; | Event handler that is triggered whenever media is captured successfully. |
| MediaCaptureFailed | EventHandler&lt;string&gt; | Event handler that is triggered whenever media capture failed. |
| OnAvailable | EventHandler&lt;bool&gt; | Event handler that is triggered whenever the selected camera device availability changes. |
| ShutterCommand | [`ICommand`](xref:Xamarin.Forms.ICommand) | Gets or sets a `Command` that is invoked when the shutter is triggered. |
| IsBusy | bool | Gets or sets if the camera is currently busy capturing media. |
| IsAvailable | bool | Gets or sets if the camera device is currently available for use. |
| CameraOptions | CameraOptions | Gets or sets which camera device should be used for the CameraView. |
| CaptureMode | CameraCaptureMode | Gets or sets the capture mode for the CameraView. Either default, video or photo. |
| VideoStabilization | bool | Gets or sets the video stabilization on the camera of the CameraView. |
| FlashMode | CameraFlashMode | Gets or sets the flash mode of the CameraView. |
| Zoom | double | Gets or sets the current zoom level of the CameraView. |
| MaxZoom | double | Gets or sets the maximum zoom level of the AvatarView. |

## Sample

[CameraView sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Views/CameraViewPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [CameraView source code](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/CameraView)
