---
title: "Xamarin Community Toolkit WeakEventManagerExtensions"
author: brminnick
ms.author: bramin
description: "Extension methods for Xamarin.Forms.WeakEventManager."
ms.date: 11/20/2020
---

# Xamarin Community Toolkit WeakEventManagerExtensions

Extension methods for the Xamarin.Forms.WeakEventManager type.

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| RaiseEvent(this Xamarin.Forms.WeakEventManager, object, object, string | void | Invokes the event EventHandler. |

## Examples

```csharp
readonly weakEventManager = new Xamarin.Forms.WeakEventManager();

public event EventHandler MyEvent
{
    add => weakEventManager.AddEventHandler(value);
    remove => weakEventManager.RemoveEventHandler(value);
}

void OnEvent() => weakEventManager.RaiseEvent(this, EventArgs.Empty, nameof(MyEvent));
```

## API

- [WeakEventManagerExtensions](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/WeakEventManager.shared.cs)

## Related links

- [DelegateWeakEventManager](delegateweakeventmanager.md)
- [WeakEventManager&lt;T&gt;](weakeventmanagert.md)
