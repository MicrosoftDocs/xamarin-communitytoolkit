---
title: "Xamarin Community Toolkit EventToCommandBehavior"
author: sthewissen
ms.author: joverslu
description: "The EventToCommandBehavior allows the user to invoke a Command through an event."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit EventToCommandBehavior

The EventToCommandBehavior is a behavior that allows the user to invoke a Command through an event. It is designed to associate Commands to events exposed by controls that were not designed to support Commands. It allows you to map any arbitrary event on a control to a Command.

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

- [ItemSelectedEventArgsConverter](~/converters/itemselectedeventargsconverter.md)
- [ItemTappedEventArgsConverter](~/converters/itemtappedeventargsconverter.md)

```xml
<ListView.Behaviors>
    <behaviors:EventToCommandBehavior
        EventName="ItemSelected"
        Command="{Binding ItemSelectedCommand}"
        EventArgsConverter="{StaticResource ItemSelectedEventArgsConverter}"
    />
</ListView.Behaviors>
```

```xml
<ListView.Behaviors>
    <behaviors:EventToCommandBehavior
        EventName="ItemTapped"
        Command="{Binding ItemTappedCommand}"
        EventArgsConverter="{StaticResource ItemTappedEventArgsConverter}"
     />
</ListView.Behaviors>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| EventName | string | The name of the event that should be associated with a `Command`. |
| Command | [ICommand](xref:System.Windows.Input.ICommand) | The `Command` that should be executed. |
| CommandParameter | object | An optional parameter to forward to the `Command`. |
| EventArgsConverter | [IValueConverter](xref:Xamarin.Forms.IValueConverter) | An optional `IValueConverter` that can be used to convert `EventArgs` values to values passed into the `Command`. |

## Sample

- [EventToCommandBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Behaviors/EventToCommandBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [EventToCommandBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/EventToCommandBehavior.shared.cs)
