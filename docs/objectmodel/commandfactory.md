---
title: "Xamarin Community Toolkit CommandFactory"
author: maxkoshevoi
ms.author: v-makkos
description: "Unify creation of Command, AsyncCommand and AsyncValueCommand."
ms.date: 2/20/2021
---

# Xamarin Community Toolkit CommandFactory

Provides unified way of creating new instances of `Command`, `AsyncCommand` and `AsyncValueCommand`


## Examples

To use it just replace `new Command`, `new AsyncCommand` and `new AsyncValueCommand` with `CommandFactory.Create`

```csharp
Command command = CommandFactory.Create(() => Debug.WriteLine("Command executed"));
Command<string> commandWithParameter = CommandFactory.Create<string>(p => Debug.WriteLine("Command executed: {0}", p));

IAsyncCommand asyncCommand = CommandFactory.Create(ExecuteCommandAsync)
IAsyncCommand<int> asyncCommandWithParameter = CommandFactory.Create<int>(ExecuteCommandAsync)

async Task ExecuteCommandAsync()
{
    // ...
}

async Task ExecuteCommandAsync(string commandParameter)
{
    // ...
}
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| Create(Action) | Command | Initializes Xamarin.Forms.Command. |
| Create(Action, Func&lt;bool&gt;) | Command | Initializes Xamarin.Forms.Command. |
| Create(Action&lt;object&gt;) | Command | Initializes Xamarin.Forms.Command. |
| Create(Action&lt;object&gt;, Func&lt;object, bool&gt;) | Command | Initializes Xamarin.Forms.Command. |
| Create&lt;T&gt;(Action&lt;T&gt;) | Command&lt;T&gt; | Initializes Xamarin.Forms.Command&lt;T&gt;. |
| Create&lt;T&gt;(Action&lt;T&gt;, Func&lt;T, bool&gt;) | Command&lt;T&gt; | Initializes Xamarin.Forms.Command&lt;T&gt;. |
| Create(Func&lt;Task&gt; execute, Func&lt;object, bool&gt; canExecute = null, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncCommand | Initializes a new instance of IAsyncCommand. |
| Create(Func&lt;Task&gt; execute, Func&lt;bool&gt; canExecute, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncCommand | Initializes a new instance of IAsyncCommand. |
| Create&lt;TExecute&gt;(Func&lt;TExecute, Task&gt; execute, Func&lt;object, bool&gt; canExecute = null, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncCommand&lt;TExecute&gt; | Initializes a new instance of IAsyncCommand&lt;TExecute&gt;. |
| Create&lt;TExecute&gt;(Func&lt;TExecute, Task&gt; execute, Func&lt;bool&gt; canExecute, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncCommand&lt;TExecute&gt; | Initializes a new instance of IAsyncCommand&lt;TExecute&gt;. |
| Create&lt;TExecute, TCanExecute&gt;(Func&lt;TExecute, Task&gt; execute, Func&lt;TCanExecute, bool&gt; canExecute = null, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncCommand&lt;TExecute, TCanExecute&gt; | Initializes a new instance of IAsyncCommand&lt;TExecute, TCanExecute&gt;. |
| Create(Func&lt;ValueTask&gt;, Func&lt;object, bool&gt; canExecute = null, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncValueCommand | Initializes a new instance of IAsyncValueCommand. |
| Create(Func&lt;ValueTask&gt; execute, Func&lt;bool&gt; canExecute, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncValueCommand | Initializes a new instance of IAsyncValueCommand. |
| Create&lt;TExecute&gt;(Func&lt;TExecute, ValueTask&gt; execute, Func&lt;object, bool&gt; canExecute = null, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncValueCommand&lt;TExecute&gt; | Initializes a new instance of IAsyncValueCommand&lt;TExecute&gt;. |
| Create&lt;TExecute&gt;(Func&lt;TExecute, ValueTask&gt; execute, Func&lt;bool&gt; canExecute, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncValueCommand&lt;TExecute&gt; | Initializes a new instance of IAsyncValueCommand&lt;TExecute&gt;. |
| Create&lt;TExecute, TCanExecute&gt;(Func&lt;TExecute, ValueTask&gt; execute, Func&lt;TCanExecute, bool&gt; canExecute = null, Action&lt;Exception&gt; onException = null, bool continueOnCapturedContext = false, bool allowsMultipleExecutions = true) | IAsyncValueCommand&lt;TExecute, TCanExecute&gt; | Initializes a new instance of IAsyncValueCommand&lt;TExecute, TCanExecute&gt;. |

## API

- [CommandFactory.Command](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/CommandFactory.Command.shared.cs)
- [CommandFactory.IAsyncCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/CommandFactory.IAsyncCommand.shared.cs)
- [CommandFactory.IAsyncValueCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/CommandFactory.IAsyncValueCommand.shared.cs)

## Related links

- [AsyncCommand](asynccommand.md)
- [AsyncValueCommand](asyncvaluecommand.md)