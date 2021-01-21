---
title: "Xamarin Community Toolkit DelegateWeakEventManager"
author: brminnick
ms.author: bramin
description: "A Delegate event implementation that enables the garbage collector to collect an object without needing to unsubscribe event handlers."
ms.date: 11/20/2020
---

# Xamarin Community Toolkit DelegateWeakEventManager

An `event Delegate` implementation that enables the [garbage collector to collect an object without needing to unsubscribe event handlers](http://paulstovell.com/blog/weakevents).

Inspired by [Xamarin.Forms.WeakEventManager](https://github.com/xamarin/Xamarin.Forms/blob/master/Xamarin.Forms.Core/WeakEventManager.cs), expanding the functionality of Xamarin.Forms.WeakEventManager to support `Delegate` events.

## Syntax

```csharp
public DelegateWeakEventManager()
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| AddEventHandler(Delegate, string eventName) | void | Adds the event handler. |
| RemoveEventHandler(Delegate, string eventName) | void | Removes the event handler. |
| HandleEvent(object, object, string | void | Invokes the event EventHandler. |
| HandleEvent(string | void | Invokes the event Action. |
| RaiseEvent(object, object, string | void | Invokes the event EventHandler. |
| RaiseEvent(string | void | Invokes the event Action. |

## Examples

This section shows how to use this type.

### Use Delegate

```csharp
readonly DelegateWeakEventManager _propertyChangedEventManager = new DelegateWeakEventManager();

public event PropertyChangedEventHandler? PropertyChanged
{
    add => _propertyChangedEventManager.AddEventHandler(value);
    remove => _propertyChangedEventManager.RemoveEventHandler(value);
}

void OnPropertyChanged([CallerMemberName]string propertyName = "") => _propertyChangedEventManager.RaiseEvent(this, new PropertyChangedEventArgs(propertyName), nameof(PropertyChanged));
```

### Use EventHandler

```csharp
readonly DelegateWeakEventManager _canExecuteChangedEventManager = new DelegateWeakEventManager();

public event EventHandler CanExecuteChanged
{
    add => _canExecuteChangedEventManager.AddEventHandler(value);
    remove => _canExecuteChangedEventManager.RemoveEventHandler(value);
}

void OnCanExecuteChanged() => _canExecuteChangedEventManager.RaiseEvent(this, EventArgs.Empty, nameof(CanExecuteChanged));
```

### Use Action

```csharp
readonly DelegateWeakEventManager _weakActionEventManager = new DelegateWeakEventManager();

public event Action ActionEvent
{
    add => _weakActionEventManager.AddEventHandler(value);
    remove => _weakActionEventManager.RemoveEventHandler(value);
}

void OnActionEvent(string message) => _weakActionEventManager.RaiseEvent(message, nameof(ActionEvent));
```

## API

- [DelegateWeakEventManager](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/DelegateWeakEventManager.shared.cs)

## Related links

- [WeakEventManager<T>](weakeventmanagert.md)
