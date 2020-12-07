---
title: "Xamarin Community Toolkit EventToCommandBehavior"
author: sthewissen
ms.author: joverslu
description: "The EventToCommandBehavior allows the user to invoke a Command through an event."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit EventToCommandBehavior

The EventToCommandBehavior is a behavior that allows the user to invoke a Command through an event.It is designed to associate Commands to events exposed by controls that were not designed with Commands in mind. It allows you to map any arbitrary event on a control to a Command.

## Syntax

This behavior can be used on any control that exposes events, such as a `Button`:

```xml
<Button.Behaviors>
    <xct:EventToCommandBehavior
        EventName="Clicked"
        Command="{Binding MyCustomCommand}" />
</Button.Behaviors>
```

When using this behavior with selection or tap events exposed by `ListView` an additional converter is required. This converter converts the event arguments to a command parameter which is then passed onto the Command. They are also available in the Xamarin Community Toolkit:

- [ItemSelectedEventArgsConverter](/xamarin-communitytoolkit/converters/itemselectedeventargsconverter)
- [ItemTappedEventArgsConverter](/xamarin-communitytoolkit/converters/itemtappedeventargsconverter)

```xml
<ListView.Behaviors>
    <behaviors:EventToCommandBehavior EventName="ItemSelected"
                                      Command="{Binding ItemSelectedCommand}"
                                      EventArgsConverter="{StaticResource ItemSelectedEventArgsConverter}" />
</ListView.Behaviors>
```

```xml
<ListView.Behaviors>
    <behaviors:EventToCommandBehavior EventName="ItemTapped"
                                      Command="{Binding ItemTappedCommand}"
                                      EventArgsConverter="{StaticResource ItemTappedEventArgsConverter}" />
</ListView.Behaviors>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| EventName | string | *Description* |
| Command | [ICommand](xref:System.Windows.Input.ICommand) | Description |
| CommandParameter | object | *Description* |
| EventArgsConverter | [IValueConverter](xref:Xamarin.Forms.IValueConverter) | *Description* |

## Sample

- [EventToCommandBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/EventToCommandBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [EventToCommandBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/EventToCommandBehavior.shared.cs)