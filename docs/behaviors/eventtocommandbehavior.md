---
title: EventToCommandBehavior
author: AlexHedley
description: .
---

# EventToCommandBehavior

## Syntax

```xaml
<Button.Behaviors>
    <behaviors:EventToCommandBehavior
        EventName="Clicked"
        Command="{Binding IncrementCommand}" />
</Button.Behaviors>
```

```xaml
<ListView.Behaviors>
    <behaviors:EventToCommandBehavior EventName="ItemSelected"
                                      Command="{Binding ItemSelectedCommand}"
                                      EventArgsConverter="{StaticResource ItemSelectedEventArgsConverter}" />
</ListView.Behaviors>
```

```xaml
<ListView.Behaviors>
    <behaviors:EventToCommandBehavior EventName="ItemTapped"
                                      Command="{Binding ItemTappedCommand}"
                                      EventArgsConverter="{StaticResource ItemTappedEventArgsConverter}" />
</ListView.Behaviors>
```

```csharp

```

## Sample output

<!-- Image/Text can show the output of the control/helper -->

## Properties

| Property | Type | Description |
| -- | -- | -- |
| EventNameProperty | BindableProperty | *Description* |
| CommandProperty | BindableProperty | Description |
| CommandParameterProperty | BindableProperty | *Description* |
| eventHandler | Delegate | *Description* |
| eventInfo | EventInfo | *Description* |
| EventName | string | *Description* |
| Command | ICommand | *Description* |
| CommandParameter | object | *Description* |

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| OnAttachedTo(View) | void | *Description* |
| OnDetachingFrom(View) | void | *Description* |


## Events

| Events | Description |
| -- | -- |
| OnEventNamePropertyChanged(BindableObject, object, object) | void | *Description* |
| RegisterEvent() | void | *Description* |
| UnregisterEvent() | void | *Description* |
| OnTriggerHandled(object, object) | void | *Description* |

## Examples

<!-- All control/helper must at least have an example to show the use of Properties and Methods in your control/helper with the output -->

## Sample project

- [EventToCommandBehaviorPage](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Behaviors/EventToCommandBehaviorPage.xaml)
- [ItemSelectedEventArgsPage](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/ItemSelectedEventArgsPage.xaml)
- [ItemTappedEventArgsPage](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Converters/ItemTappedEventArgsPage.xaml)

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [EventToCommandBehavior]([source-code-link](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Behaviors/EventToCommandBehavior.shared.cs))
