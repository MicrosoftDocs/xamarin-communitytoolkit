---
title: "Xamarin Community Toolkit CommandFactory"
author: maxkoshevoi
ms.author: joverslu
description: "The CommandFactory class provides a unified approach to creating new Command, AsyncCommand, and AsyncValueCommand objects."
ms.date: 2/20/2021
---

# Xamarin Community Toolkit CommandFactory

The `CommandFactory` class provides a unified approach to creating new `Command`, `AsyncCommand,` and `AsyncValueCommand` objects.

## Syntax

```csharp
public static CommandFactory.Create()
```

## Examples

To consume the `CommandFactory` class, replace `new Command`, `new AsyncCommand` and `new AsyncValueCommand` with the `CommandFactory.Create` method:

```csharp
Command command = CommandFactory.Create(() => Debug.WriteLine("Command executed"));
Command<string> commandWithParameter = CommandFactory.Create<string>(p => Debug.WriteLine("Command executed: {0}", p));

IAsyncCommand asyncCommand = CommandFactory.Create(ExecuteCommandAsync)
IAsyncCommand<int> asyncCommandWithParameter = CommandFactory.Create<int>(ExecuteCommandAsync)

async Task ExecuteCommandAsync()
{
    // ...
}

async Task ExecuteCommandAsync(int commandParameter)
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

## Sample project

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/samples/XCT.Sample).
In the sample app, every command is created using this approach. For more information, see [BasePage Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Base/BasePage.cs) as an example.

## API

- [CommandFactory.Command](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/CommandFactory.Command.shared.cs)
- [CommandFactory.IAsyncCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/CommandFactory.IAsyncCommand.shared.cs)
- [CommandFactory.IAsyncValueCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/CommandFactory.IAsyncValueCommand.shared.cs)

## Related links

- [AsyncCommand](asynccommand.md)
- [AsyncValueCommand](asyncvaluecommand.md)
