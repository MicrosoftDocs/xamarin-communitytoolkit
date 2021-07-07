---
title: "Xamarin Community Toolkit MediaElement"
description: "This article explains how to use MediaElement to play video and audio in a Xamarin.Forms application."
author: jfversluis
ms.author: joverslu
ms.date: 10/21/2020
---

# Xamarin Community Toolkit MediaElement

[![Download Sample.](~/images/download.png) Download the sample](/samples/xamarin/xamarin-forms-samples/userinterface-mediaelementdemos/)

`MediaElement` is a view for playing video and audio. Media that's supported by the underlying platform can be played from the following sources:

- The web, using a URI (HTTP or HTTPS).
- A resource embedded in the platform application, using the `ms-appx:///` URI scheme.
- Files that come from the app's local and temporary data folders, using the `ms-appdata:///` URI scheme.
- The device's library.

`MediaElement` can use the platform playback controls, which are referred to as transport controls. However, they are disabled by default and can be replaced with your own transport controls. The following screenshots show `MediaElement` playing a video with the platform transport controls:

[![Screenshot of a MediaElement playing a video, on iOS and Android.](mediaelement-images/playback-controls.png](mediaelement-images/playback-controls-large.png#lightbox)

> [!NOTE]
> `MediaElement` is available on iOS, Android, the Universal Windows Platform (UWP), macOS, Windows Presentation Foundation, and Tizen.

`MediaElement` defines the following properties:

- `Aspect`, of type [`Aspect`](xref:Xamarin.Forms.Aspect), determines how the media will be scaled to fit the display area. The default value of this property is `AspectFit`.
- `AutoPlay`, of type `bool`, indicates whether media playback will begin automatically when the `Source` property is set. The default value of this property is `true`.
- `BufferingProgress`, of type `double`, indicates the current buffering progress. The default value of this property is 0.0.
- `CanSeek`, of type `bool`, indicates whether media can be repositioned by setting the value of the `Position` property. This is a read-only property.
- `CurrentState`, of type `MediaElementState`, indicates the current status of the control. This is a read-only property, whose default value is `MediaElementState.Closed`.
- `Duration`, of type `TimeSpan?`, indicates the duration of the currently opened media. This is a read-only property whose default value is `null`.
- `IsLooping`, of type `bool`, describes whether the currently loaded media source should resume playback from the start after reaching its end. The default value of this property is `false`.
- `KeepScreenOn`, of type `bool`, determines whether the device screen should stay on during media playback. The default value of this property is `false`.
- `Position`, of type `TimeSpan`, describes the current progress through the media's playback time. This property uses a `TwoWay` binding, and its default value is `TimeSpan.Zero`.
- `ShowsPlaybackControls`, of type `bool`, determines whether the platforms playback controls are displayed. The default value of this property is `false`. Note that on iOS the controls are only shown for a brief period after interacting with the screen. There is no way of keeping the controls visible at all times. On WPF, no system controls are supported so this property has no effect.
- `Source`, of type `MediaSource`, indicates the source of the media loaded into the control.
- `VideoHeight`, of type `int`, indicates the height of the control. This is a read-only property.
- `VideoWidth`, of type `int`, indicates the width of the control. This is a read-only property.
- `Volume`, of type `double`, determines the media's volume, which is represented on a linear scale between 0 and 1. This property uses a `TwoWay` binding, and its default value is 1.

These properties, with the exception of the `CanSeek` property, are backed by [`BindableProperty`](xref:Xamarin.Forms.BindableProperty) objects, which means that they can be targets of data bindings, and styled.

The `MediaElement` class also defines four events:

- `MediaOpened` is fired when the media stream has been validated and opened.
- `MediaEnded` is fired when the `MediaElement` finishes playing its media.
- `MediaFailed` is fired when there's an error associated with the media source.
- `SeekCompleted` is fired when the seek point of a requested seek operation is ready for playback.

In addition, `MediaElement` includes `Play`, `Pause`, and `Stop` methods.

For information about supported media formats on Android, see [Supported media formats](https://developer.android.com/guide/topics/media/media-formats) on developer.android.com. For information about supported media formats on the Universal Windows Platform (UWP), see [Supported codecs](/windows/uwp/audio-video-camera/supported-codecs).

## Play remote media

A `MediaElement` can play remote media files using the HTTP and HTTPS URI schemes. This is accomplished by setting the `Source` property to the URI of the media file:

```xaml
<MediaElement Source="https://sec.ch9.ms/ch9/5d93/a1eab4bf-3288-4faf-81c4-294402a85d93/XamarinShow_mid.mp4"
              ShowsPlaybackControls="True" />
```

By default, the media that is defined by the `Source` property plays immediately after the media is opened. To suppress automatic media playback, set the `AutoPlay` property to `false`.

Media playback controls are disabled by default, and are enabled by setting the `ShowsPlaybackControls` property to `true`. `MediaElement` will then use the platform playback controls where available.

## Play local media

Local media can be played from the following sources:

- A resource embedded in the platform application, using the `ms-appx:///` URI scheme.
- Files that come from the app's local and temporary data folders, using the `ms-appdata:///` URI scheme.
- The device's library.

For more information about these URI schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes).

### Play media embedded in the app package

A `MediaElement` can play media files that are embedded in the app package, using the `ms-appx:///` URI scheme. Media files are embedded in the app package by placing them in the platform project.

Storing a media file in the platform project is different for each platform:

- On iOS, media files must be stored in the **Resources** folder, or a subfolder of the **Resources** folder. The media file must have a `Build Action` of `BundleResource`.
- On Android, media files must be stored in a subfolder of **Resources** named **raw**. The **raw** folder cannot contain subfolders. The media file must have a `Build Action` of `AndroidResource`.
- On UWP, media files can be stored in any folder in the project. The media file must have a `BuildAction` of `Content`.

Media files that meet these criteria can then be played back using the `ms-appx:///` URI scheme:

```xaml
<MediaElement Source="ms-appx:///XamarinForms101UsingEmbeddedImages.mp4"
              ShowsPlaybackControls="True" />
```

When using data binding, a value converter can be used to apply this URI scheme:

```csharp
public class VideoSourceConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        if (value == null)
            return null;

        if (string.IsNullOrWhiteSpace(value.ToString()))
            return null;

        if (Device.RuntimePlatform == Device.UWP)
            return new Uri($"ms-appx:///Assets/{value}");
        else
            return new Uri($"ms-appx:///{value}");
    }
    // ...
}
```

An instance of the `VideoSourceConverter` can then be used to apply the `ms-appx:///` URI scheme to an embedded media file:

```xaml
<MediaElement Source="{Binding MediaSource, Converter={StaticResource VideoSourceConverter}}"
              ShowsPlaybackControls="True" />
```

For more information about the ms-appx URI scheme, see [ms-appx and ms-appx-web](/windows/uwp/app-resources/uri-schemes#ms-appx-and-ms-appx-web).

### Play media from the app's local and temporary folders

A `MediaElement` can play media files that are copied into the app's local or temporary data folders, using the `ms-appdata:///` URI scheme.

The following example shows the `Source` property set to a media file that's stored in the app's local data folder:

```xaml
<MediaElement Source="ms-appdata:///local/XamarinVideo.mp4"
              ShowsPlaybackControls="True" />
```

The following example shows the `Source` property to a media file that's stored in the app's temporary data folder:

```xaml
<MediaElement Source="ms-appdata:///temp/XamarinVideo.mp4"
              ShowsPlaybackControls="True" />
```

> [!IMPORTANT]
> In addition to playing media files that are stored in the app's local or temporary data folders, UWP can also play media files that are located in the app's roaming folder. This can be achieved by prefixing the media file with `ms-appdata:///roaming/`.

When using data binding, a value converter can be used to apply this URI scheme:

```csharp
public class VideoSourceConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        if (value == null)
            return null;

        if (string.IsNullOrWhiteSpace(value.ToString()))
            return null;

        return new Uri($"ms-appdata:///{value}");
    }
    // ...
}
```

An instance of the `VideoSourceConverter` can then be used to apply the `ms-appdata:///` URI scheme to a media file in the app's local or temporary data folder:

```xaml
<MediaElement Source="{Binding MediaSource, Converter={StaticResource VideoSourceConverter}}"
              ShowsPlaybackControls="True" />
```

For more information about the ms-appdata URI scheme, see [ms-appdata](/windows/uwp/app-resources/uri-schemes#ms-appdata).

#### Copying a media file to the app's local or temporary data folder

Playing a media file stored in the app's local or temporary data folder requires the media file to be copied there by the app. This can be accomplished, for example, by copying a media file from the app package:

```csharp
// This method copies the video from the app package to the app data
// directory for your app. To copy the video to the temp directory
// for your app, comment out the first line of code, and uncomment
// the second line of code.
public static async Task CopyVideoIfNotExists(string filename)
{
    string folder = FileSystem.AppDataDirectory;
    //string folder = Path.GetTempPath();
    string videoFile = Path.Combine(folder, "XamarinVideo.mp4");

    if (!File.Exists(videoFile))
    {
        using (Stream inputStream = await FileSystem.OpenAppPackageFileAsync(filename))
        {
            using (FileStream outputStream = File.Create(videoFile))
            {
                await inputStream.CopyToAsync(outputStream);
            }
        }
    }
}
```

> [!NOTE]
> The code example above uses the `FileSystem` class included in Xamarin.Essentials. For more information, see [Xamarin.Essentials: File System Helpers](/xamarin/essentials/file-system-helpers?context=xamarin%2Fxamarin-forms&tabs=android).

### Play media from the device library

Most modern mobile devices and desktop computers have the ability to record videos and audio using the device's camera and microphone. The media that's created are then stored as files on the device. These files can be retrieved from the library and played by the `MediaElement`.

Each of the platforms includes a facility that allows the user to select media from the device's library. In Xamarin.Forms, platform projects can invoke this functionality, and it can be called by the [`DependencyService`](xref:Xamarin.Forms.DependencyService) class.

The video picking dependency service used in the sample application is very similar to one defined in [Picking a Photo from the Picture Library](/xamarin/xamarin-forms/app-fundamentals/dependency-service/photo-picker), except that the picker returns a filename rather than a `Stream` object. The shared code project defines an interface named `IVideoPicker`, that defines a single method named `GetVideoFileAsync`. Each platform then implements this interface in a `VideoPicker` class.

The following code example shows how to retrieve a media file from the device library:

```csharp
string filename = await DependencyService.Get<IVideoPicker>().GetVideoFileAsync();
if (!string.IsNullOrWhiteSpace(filename))
{
    mediaElement.Source = new FileMediaSource
    {
        File = filename
    };
}
```

The video picking dependency service is invoked by calling the `DependencyService.Get` method to obtain the implementation of an `IVideoPicker` interface in the platform project. The `GetVideoFileAsync` method is then called on that instance, and the returned filename is used to create a `FileMediaSource` object and to set it to the `Source` property of the `MediaElement`.

## Change video aspect ratio

The `Aspect` property determines how video media will be scaled to fit the display area. By default, this property is set to the `AspectFit` enumeration member, but it can be set to any of the [`Aspect`](xref:Xamarin.Forms.Aspect) enumeration members:

- `AspectFit` indicates that the video will be letterboxed, if required, to fit into the display area, while preserving the aspect ratio.
- `AspectFill` indicates that the video will be clipped so that it fills the display area, while preserving the aspect ratio.
- `Fill` indicates that the video will be stretched to fill the display area.

## Binding to the Position property

The property change notification for the `Position` bindable property fire at 200ms intervals while playing. Therefore, the property can be data-bound to a `Slider` control (or similar) to show progress through the media. The CommunityToolkit also provides a [`TimeSpanToDoubleConverter`](xref:Xamarin.CommunityToolkit.Converters.TimeSpanToDoubleConverter) which converts a [`TimeSpan`](xref:System.TimeSpan) into a floating point value representing total seconds elapsed. In this way you can set the Slider `Maximum` to the `Duration` of the media and the `Value` to the `Position` to provide accurate progress:

```xaml
<?xml version="1.0" encoding="UTF-8"?>
<pages:BasePage xmlns="http://xamarin.com/schemas/2014/forms"
                xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
                xmlns:pages="clr-namespace:Xamarin.CommunityToolkit.Sample.Pages"
                x:Class="Xamarin.CommunityToolkit.Sample.Pages.Views.MediaElementPage">
    <pages:BasePage.Resources>
        <xct:TimeSpanToDoubleConverter x:Key="TimeSpanConverter"/>
    </pages:BasePage.Resources>
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="*"/>
            <RowDefinition Height="*"/>
            <RowDefinition Height="Auto"/>
        </Grid.RowDefinitions>
        <xct:MediaElement
            x:Name="mediaElement"
            Source="https://sec.ch9.ms/ch9/5d93/a1eab4bf-3288-4faf-81c4-294402a85d93/XamarinShow_mid.mp4"
            ShowsPlaybackControls="True"
            HorizontalOptions="Fill"
            SeekCompleted="OnSeekCompleted" />
        <Slider Grid.Row="1" BindingContext="{x:Reference mediaElement}" Value="{Binding Position, Converter={StaticResource TimeSpanConverter}}" Maximum="{Binding Duration, Converter={StaticResource TimeSpanConverter}}">
            <Slider.Triggers>
                <DataTrigger TargetType="Slider"
                     Binding="{Binding CurrentState}"
                     Value="{x:Static MediaElementState.Buffering}">
                    <Setter Property="IsEnabled" Value="False" />
                </DataTrigger>
            </Slider.Triggers>
        </Slider>
        <Button Grid.Row="2" Text="Reset Source (Set Null)" Clicked="OnResetClicked" />
    </Grid>
</pages:BasePage>
```

In this example, the `Maximum` property of the `Slider` is data-bound to the `Duration` property of the `MediaElement` and the [`Value`](xref:Xamarin.Forms.Slider.Value) property of the [`Slider`](xref:Xamarin.Forms.Slider) is data-bound to the `Position` property of the `MediaElement`. Therefore, dragging the `Slider` results in the media playback position changing:

[![Screenshot of a MediaElement with a position bar, on iOS and Android.](mediaelement-images/custom-position-bar.png](mediaelement-images/custom-position-bar-large.png#lightbox)

In addition, a [`DataTrigger`](xref:Xamarin.Forms.DataTrigger) object is used to disable the `Slider` when the media is buffering. For more information about data triggers, see [Xamarin.Forms Triggers](/xamarin/xamarin-forms/app-fundamentals/triggers).

> [!NOTE]
> On Android, the [`Slider`](xref:Xamarin.Forms.Slider) only has 1000 discrete steps, regardless of the `Minimum` and `Maximum` settings. If the media length is greater than 1000 seconds, then two different `Position` values would correspond to the same `Value` of the `Slider`. This is why the code above checks that the new position and existing position are greater than one-hundredth of the overall duration.

## Understand MediaSource types

A `MediaElement` can play media by setting its `Source` property to a remote or local media file. The `Source` property is of type `MediaSource`, and this class defines two static methods:

- `FromFile`, returns a `MediaSource` instance from a `string` argument.
- `FromUri`, returns a `MediaSource` instance from a `Uri` argument.

In addition, the `MediaSource` class also has implicit operators that return `MediaSource` instances from `string` and `Uri` arguments.

> [!NOTE]
> When the `Source` property is set in XAML, a type converter is invoked to return a `MediaSource` instance from a `string` or `Uri`.

The `MediaSource` class also has two derived classes:

- `UriMediaSource`, which is used to specify a remote media file from a URI. This class has a `Uri` property that can be set to a `Uri`.
- `FileMediaSource`, which is used to specify a local media file from a `string`. This class has a `File` property that can be set to a `string`. In addition, this class has implicit operators to convert a `string` to a `FileMediaSource` object, and a `FileMediaSource` object to a `string`.

> [!NOTE]
> When a `FileMediaSource` object is created in XAML, a type converter is invoked to return a `FileMediaSource` instance from a `string`.

## Determine MediaElement status

The `MediaElement` class defines a read-only bindable property named `CurrentState`, of type `MediaElementState`. This property indicates the current status of the control, such as whether the media is playing or paused, or if it's not yet ready to play the media.

The `MediaElementState` enumeration defines the following members:

- `Closed` indicates that the `MediaElement` contains no media.
- `Opening` indicates that the `MediaElement` is validating and attempting to load the specified source.
- `Buffering` indicates that the `MediaElement` is loading the media for playback. Its `Position` property does not advance during this state. If the `MediaElement` was playing video, it continues to display the last displayed frame.
- `Playing` indicates that the `MediaElement` is playing the media source.
- `Paused` indicates that the `MediaElement` does not advance its `Position` property. If the `MediaElement` was playing video, it continues to display the current frame.
- `Stopped` indicates that the `MediaElement` contains media but it is not being played or paused. Its `Position` property is 0 and does not advance. If the loaded media is video, the `MediaElement` displays the first frame.

It's generally not necessary to examine the `CurrentState` property when using the `MediaElement` transport controls. However, this property becomes important when implementing your own transport controls.

## Implement custom transport controls

The transport controls of a media player include the buttons that perform the functions **Play**, **Pause**, and **Stop**. These buttons are generally identified with familiar icons rather than text, and the **Play** and **Pause** functions are generally combined into one button.

By default, the `MediaElement` playback controls are disabled. This enables you to control the `MediaElement` programmatically, or by supplying your own transport controls. In support of this, `MediaElement` includes `Play`, `Pause`, and `Stop` methods.

The following XAML example shows a page that contains a `MediaElement` and custom transport controls:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MediaElementDemos.CustomTransportPage"
             Title="Custom transport">
    <Grid>
        ...
        <MediaElement x:Name="mediaElement"
                      AutoPlay="False"
                      ... />
        <StackLayout BindingContext="{x:Reference mediaElement}"
                     ...>
            <Button Text="&#x25B6;&#xFE0F; Play"
                    HorizontalOptions="CenterAndExpand"
                    Clicked="OnPlayPauseButtonClicked">
                <Button.Triggers>
                    <DataTrigger TargetType="Button"
                                 Binding="{Binding CurrentState}"
                                 Value="{x:Static MediaElementState.Playing}">
                        <Setter Property="Text"
                                Value="&#x23F8; Pause" />
                    </DataTrigger>
                    <DataTrigger TargetType="Button"
                                 Binding="{Binding CurrentState}"
                                 Value="{x:Static MediaElementState.Buffering}">
                        <Setter Property="IsEnabled"
                                Value="False" />
                    </DataTrigger>
                </Button.Triggers>
            </Button>
            <Button Text="&#x23F9; Stop"
                    HorizontalOptions="CenterAndExpand"
                    Clicked="OnStopButtonClicked">
                <Button.Triggers>
                    <DataTrigger TargetType="Button"
                                 Binding="{Binding CurrentState}"
                                 Value="{x:Static MediaElementState.Stopped}">
                        <Setter Property="IsEnabled"
                                Value="False" />
                    </DataTrigger>
                </Button.Triggers>
            </Button>
        </StackLayout>
    </Grid>
</ContentPage>
```

In this example, the custom transport controls are defined as [`Button`](xref:Xamarin.Forms.Button) objects. However, there are only two `Button` objects, with the first `Button` representing **Play** and **Pause**, and the second `Button` representing **Stop**. [`DataTrigger`](xref:Xamarin.Forms.DataTrigger) objects are used to enable and disable the buttons, and to switch the first button between **Play** and **Pause**. For more information about data triggers, see [Xamarin.Forms Triggers](/xamarin/xamarin-forms/app-fundamentals/triggers).

The code-behind file has the handlers for the [`Clicked`](xref:Xamarin.Forms.Button.Clicked) events:

```csharp
void OnPlayPauseButtonClicked(object sender, EventArgs args)
{
    if (mediaElement.CurrentState == MediaElementState.Stopped ||
        mediaElement.CurrentState == MediaElementState.Paused)
    {
        mediaElement.Play();
    }
    else if (mediaElement.CurrentState == MediaElementState.Playing)
    {
        mediaElement.Pause();
    }
}

void OnStopButtonClicked(object sender, EventArgs args)
{
    mediaElement.Stop();
}
```

The **Play** button can be pressed, once it becomes enabled, to begin playback:

[![Screenshot of a MediaElement with custom transport controls, on iOS and Android.](mediaelement-images/custom-transport-playback.png](mediaelement-images/custom-transport-playback-large.png#lightbox)

Pressing the **Pause** button results in playback pausing:

[![Screenshot of a MediaElement with playback paused, on iOS and Android](mediaelement-images/custom-transport-paused.png "MediaElement with a paused video."](mediaelement-images/custom-transport-paused-large.png#lightbox "MediaElement with a paused video")

Pressing the **Stop** button stops playback and returns the position of the media file to the beginning.

## Implement a custom volume control

Media playback controls implemented by each platform include a volume bar. This bar resembles a slider and shows the volume of the media. In addition, you can manipulate the volume bar to increase or decrease the volume.

A custom volume bar can be implemented using a [`Slider`](xref:Xamarin.Forms.Slider), as shown in the following example:

```xaml
<StackLayout>
    <MediaElement AutoPlay="False"
                  Source="{StaticResource AdvancedAsync}" />
    <Slider Maximum="1.0"
            Minimum="0.0"
            Value="{Binding Volume}"
            Rotation="270"
            WidthRequest="100" />
</StackLayout>
```

In this example, the [`Slider`](xref:Xamarin.Forms.Slider) data binds its `Value` property to the `Volume` property of the `MediaElement`. This is possible because the `Volume` property uses a `TwoWay` binding. Therefore, changing the `Value` property will result in the `Volume` property changing.

> [!NOTE]
> The `Volume` property has a validation callback that ensures that its value is greater than or equal to 0.0, and less than or equal to 1.0.

For more information about using a [`Slider`](xref:Xamarin.Forms.Slider) see, [Xamarin.Forms Slider](/xamarin/xamarin-forms/user-interface/slider)

## Related links

- [MediaElementDemos (sample)](/samples/xamarin/xamarin-forms-samples/userinterface-mediaelementdemos/)
- [URI schemes](/windows/uwp/app-resources/uri-schemes)
- [Xamarin.Forms Triggers](/xamarin/xamarin-forms/app-fundamentals/triggers)
- [Xamarin.Forms Slider](/xamarin/xamarin-forms/user-interface/slider)
- [Android: Supported media formats](https://developer.android.com/guide/topics/media/media-formats)
- [UWP: Supported codecs](/windows/uwp/audio-video-camera/supported-codecs)
