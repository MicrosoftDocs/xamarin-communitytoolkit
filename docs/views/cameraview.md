---
title: "Xamarin Community Toolkit CameraView"
description: "The CameraView control enables the user to display a camera preview, take photos and record videos."
author: jfversluis
ms.author: joverslu
ms.date: 12/01/2020
---

# Xamarin Community Toolkit CameraView

The CameraView control enables the user to display a preview of the camera output. In addition, it can take photos or record videos. The CameraView also offers the options you would expect to support taking photos and recording videos such as turning the flash on or off, saving the captured media to a file, and offering different hooks for events.

## Syntax

```xaml
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
| CameraOptions | CameraOptions | Gets or sets which camera device should be used for the CameraView. |
| CaptureMode | CameraCaptureMode | Gets or sets the capture mode for the CameraView. Either default, video or photo. |
| FlashMode | CameraFlashMode | Gets or sets the flash mode of the CameraView. |
| IsAvailable | bool | Gets or sets if the camera device is currently available for use. |
| IsBusy | bool | Gets or sets if the camera is currently busy capturing media. |
| MaxZoom | double | Gets or sets the maximum zoom level of the CameraView. |
| ShutterCommand | [`ICommand`](xref:System.Windows.Input.ICommand) | Gets or sets a `Command` that is invoked when the shutter is triggered. |
| VideoStabilization | bool | Gets or sets the video stabilization on the camera of the CameraView. |
| Zoom | double | Gets or sets the current zoom level of the CameraView. |

## Events

| Event  |Type  |Description  |
|---------|---------|---------|
| MediaCaptured | EventHandler&lt;MediaCapturedEventArgs&gt; | Event that is triggered whenever media is captured successfully. |
| MediaCaptureFailed | EventHandler&lt;string&gt; | Event that is triggered whenever media capture failed. |
| OnAvailable | EventHandler&lt;bool&gt; | Event that is triggered whenever the selected camera device availability changes. |

## Sample

[CameraView sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Views/CameraViewPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [CameraView source code](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/CameraView)
