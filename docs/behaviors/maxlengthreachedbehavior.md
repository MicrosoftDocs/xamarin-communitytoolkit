---
title: "Xamarin Community Toolkit MaxLengthReachedBehavior"
author: sthewissen
ms.author: joverslu
description: "The MaxLengthReachedBehavior allows the user to trigger an action when a user has reached the maximum length allowed on an Entry."
ms.date: 12/08/2020
---

# Xamarin Community Toolkit MaxLengthReachedBehavior

The MaxLengthReachedBehavior is a behavior that allows the user to trigger an action when a user has reached the maximum length allowed on an `Entry`. It can either trigger a `Command` or an `event` depending on the user's preferred scenario.

## Syntax

```xml
<<Entry 
    Placeholder="Start typing until MaxLength is reached..."
    MaxLength="10">
    <Entry.Behaviors>
        <xct:MaxLengthReachedBehavior         
            MaxLengthReached="MaxLengthReachedBehavior_MaxLengthReached"
            ShouldDismissKeyboardAutomatically="True" 
        />
    </Entry.Behaviors>
</Entry>

<Entry 
    Placeholder="Start typing until MaxLength is reached..."
    MaxLength="10">
    <Entry.Behaviors>
        <xct:MaxLengthReachedBehavior 
            Command="{Binding MaxLengthReachedCommand}"
            ShouldDismissKeyboardAutomatically="False" 
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Command | [ICommand](xref:System.Windows.Input.ICommand) | The command to execute when the user has reached the maximum length. |
| ShouldDismissKeyboardAutomatically | int | Indicates whether or not the keyboard should be dismissed automatically. |

## Events

|Event | Description  |
|---------|---------|
| MaxLengthReached | The event to raise when the user has reached the maximum length. |

## Sample

- [MaxLengthReachedBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/MaxLengthReachedBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MaxLengthReachedBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/MaxLengthReachedBehavior.shared.cs)
