---
title: "Xamarin Community Toolkit VisualElementExtension"
author: VladislavAntonyuk
ms.author: joverslu
description: "The VisualElementExtension allows users to an snackbar or toast anchored to any visual element."
ms.date: 10/09/2020
---

# Xamarin Community Toolkit VisualElementExtension

The `VisualElementExtension` is an extension that can be used to display an snackbar or toast anchored to any visual element.

### Toast ###

A toast provides simple feedback about an operation in a small popup.

There are 2 different ways to use Toast.

1. The simple - on your MyVisualElement call the method:
```csharp	
await MyVisualElement.DisplayToastAsync(message, duration);	
```	
where `message` is your text, and `duration` is the timespan of toast (an optional parameter). Default duration = 3000 milliseconds;	

![Toast WPF](visualelementextension-images/toast1.png)

2. With advanced settings you can customise Message options and Toast options:	
```csharp	
    var messageOptions = new MessageOptions	
    {	
        Foreground = Color.Black,	
        Font = Font.SystemFontOfSize(16),
        Message = "My text"	
    };	
    var options = new ToastOptions	
    {	
        MessageOptions = messageOptions,	
        Duration = TimeSpan.FromMilliseconds(3000),	
        BackgroundColor = Color.Default,	
        IsRtl = false
    };	
    await this.DisplayToastAsync(options);	
```	

![Toast GTK](visualelementextension-images/toast2.png)

### Snackbar ###

Snackbars inform users of a process that an app has performed or will perform. They appear temporarily, towards the bottom of the screen

Snackbar has API which is similar to the Toast.	

1. Simple execution with predefined settings. On your Page call the method: 	
```csharp	
var result = await MyVisualElement.DisplaySnackbarAsync(message, actionButtonText, action, duration);	
```	
where `message` is your text, `actionButtonText` is the text for the button, `action` is a `Func<Task>` and `duration` is optional parameter. Default duration = 3000 milliseconds;

The result is `Boolean`. `True` - if Snackbar is closed by the user. `False` - if Snackbar is closed by timeout.

![Snackbar iOS](visualelementextension-images/snackbar1.png)

2. With advanced settings you have a full control for all `MessageOptions`, `SnackBarActionOptions` and `SnackBarOptions`:
```csharp	
    var messageOptions = new MessageOptions	
    {	
        Foreground = Color.Black,	
        Font = Font.SystemFontOfSize(16),
        Message = "My text"	
    };	
    var actionOptions = new List<SnackBarActionOptions>	
    {	
        new SnackBarActionOptions	
        {	
            ForegroundColor = Color.Black,	
            BackgroundColor = Color.White,	
            FontFamily = Font.SystemFontOfSize(14),	
            Text = "Action 1",	
            Action = () => // null by default	
            {	
                Debug.WriteLine("1");	
                return Task.CompletedTask;	
            }	
        },
        new SnackBarActionOptions	
        {	
            ForegroundColor = Color.Black,	
            BackgroundColor = Color.White,	
            FontFamily = Font.SystemFontOfSize(16),
            Text = "Action 2",	
            Action = () => // null by default	
            {	
                Debug.WriteLine("1");	
                return Task.CompletedTask;	
            }	
        }	
    };	
    var options = new SnackbarOptions	
    {	
        MessageOptions = messageOptions,	
        Duration = TimeSpan.FromMilliseconds(3000),
        BackgroundColor = Color.Default,	
        IsRtl = false,	
        Actions = actionOptions	
    };	
    var result = await this.DisplaySnackbarAsync(options);	
```

![Snackbar UWP](visualelementextension-images/snackbar2.png)

## Details of implementation and limitation for different platforms ##

### I ###
Both Toast and Snackbar work on all platforms: Android, iOS, macOS, UWP, WPF, GTK, Tizen.

### II ###
Both Toast and Snackbar by default uses native colors and automatically change them depends on the system theme.

### III ###
"Native" Toast and Snackbar available only on Android and created by Google.

Other platforms use "Container" (UIView for iOS, NSView for macOS, Grid for WPF, HBox for GTK, Dialog foe Tizen) to display a message and action buttons.

Because of Android limitations, it has only 1 action button, while all other platforms can display multiple action buttons.

### IV ###
Android uses snackbar for both `DisplayToastAsync` and `DisplaySnackbarAsync`. The difference that `DisplayToastAsync` hides the action button.

## API

* [VisualElementExtension source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Extensions/VisualElementExtension.shared.cs)
