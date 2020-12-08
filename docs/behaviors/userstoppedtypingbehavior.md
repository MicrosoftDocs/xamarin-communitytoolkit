---
title: "Xamarin Community Toolkit UserStoppedTypingBehavior"
author: sthewissen
ms.author: joverslu
description: "The UserStoppedTypingBehavior allows the user to trigger an action when a user has stopped the input of data into an Entry."
ms.date: 12/08/2020
---

# Xamarin Community Toolkit UserStoppedTypingBehavior

The UserStoppedTypingBehavior is a behavior that allows the user to trigger an action when a user has stopped the input of data into an `Entry`. Popular examples of its usage include triggering a search when a user has stopped putting in his search query.

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:UserStoppedTypingBehavior 
            Command="{Binding SearchCommand}"
            StoppedTypingTimeThreshold="1000"
            MinimumLengthThreshold="3"
            ShouldDismissKeyboardAutomatically="True" />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Command | [ICommand](xref:System.Windows.Input.ICommand) | The command to execute when the user has stopped providing input. |
| MinimumLengthThreshold | int | The minimum length of the input value required before the command will be executed. |
| ShouldDismissKeyboardAutomatically | int | Indicates whether or not the keyboard should be dismissed automatically. |
| StoppedTypingTimeThreshold | bool | The time of inactivity in milliseconds after which the command will be executed. |


## Sample

- [UserStoppedTypingBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/UserStoppedTypingBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [UserStoppedTypingBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/UserStoppedTypingBehavior.shared.cs)