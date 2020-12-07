---
title: "Xamarin Community Toolkit WeakEventManagerExtensions"
author: brminnick
ms.author: bramin
description: "Extension methods for Xamarin.Forms.WeakEventManager"
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

## Sample project

[BaseCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/ObjectModel/BaseCommand.shared.cs). 

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API 

- [WeakEventManagerExtensions](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/WeakEventManager.shared.cs)

## Related links

- [DelegateWeakEventManager](delegateweakeventmanager.md)
- [WeakEventManager<T>](weakeventmanagert.md)
