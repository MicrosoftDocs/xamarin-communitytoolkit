---
title: "Xamarin Community Toolkit WeakEventManager<T>"
author: brminnick
ms.author: bramin
description: "An event implementation that enables the garbage collector to collect an object without needing to unsubscribe event handlers"
ms.date: 11/20/2020
---

# Xamarin Community Toolkit WeakEventManager<TEventArgs>

An event implementation that enables the [garbage collector to collect an object without needing to unsubscribe event handlers](http://paulstovell.com/blog/weakevents).

Inspired by [Xamarin.Forms.WeakEventManager](https://github.com/xamarin/Xamarin.Forms/blob/master/Xamarin.Forms.Core/WeakEventManager.cs).

## Syntax

```csharp
public WeakEventManager<TEventArgs>()
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| AddEventHandler(EventHandler<TEventArgs>, string eventName) | void | Adds the event handler |
| AddEventHandler(Action<TEventArgs>, string eventName) | void | Adds the event handler |
| RemoveEventHandler(EventHandler<TEventArgs>, string eventName) | void | Removes the event handler |
| RemoveEventHandler(Action<TEventArgs>, string eventName) | void | Removes the event handler |
| HandleEvent(object, TEventArgs, string | void | Invokes the event EventHandler |
| HandleEvent(TEventArgs, string | void | Invokes the event Action |
| RaiseEvent(object, TEventArgs, string | void | Invokes the event EventHandler |
| RaiseEvent(TEventArgs, string | void | Invokes the event Action |

## Examples

### Using `EventHandler<T>`

```csharp
readonly WeakEventManager<string> _errorOcurredEventManager = new WeakEventManager<string>();

public event EventHandler<string> ErrorOcurred
{
    add => _errorOcurredEventManager.AddEventHandler(value);
    remove => _errorOcurredEventManager.RemoveEventHandler(value);
}

void OnErrorOcurred(string message) => _errorOcurredEventManager.RaiseEvent(this, message, nameof(ErrorOcurred));
```

#### Using `Action<T>`

```csharp
readonly WeakEventManager<string> _weakActionEventManager = new WeakEventManager<string>();

public event Action<string> ActionEvent
{
    add => _weakActionEventManager.AddEventHandler(value);
    remove => _weakActionEventManager.RemoveEventHandler(value);
}

void OnActionEvent(string message) => _weakActionEventManager.RaiseEvent(message, nameof(ActionEvent));
```
## Sample project

[MaxLengthReachedBehavior](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Behaviors/MaxLengthReachedBehavior.shared.cs). 

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API 

- [WeakEventManager<T>](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/WeakEventManager.shared.cs)

## Related Links

- [DelegateWeakEventManager](../delegateweakeventmanager.md)