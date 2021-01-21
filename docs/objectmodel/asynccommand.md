---
title: "Xamarin Community Toolkit AsyncCommand"
author: brminnick
ms.author: bramin
description: "Enables the Task type to safely be used asynchronously with an ICommand."
ms.date: 11/20/2020
---

# Xamarin Community Toolkit AsyncCommand

Enables the `Task` type to safely be used asynchronously with an `ICommand`.

## Syntax

### `AsyncCommand<TExecute, TCanExecute> : IAsyncCommand<TExecute, TCanExecute>`

```csharp
public AsyncCommand(
    Func<TExecute, Task> execute,
    Func<TCanExecute, bool> canExecute = null,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
```

### `AsyncCommand<T> : IAsyncCommand<T>`

```csharp
public AsyncCommand(
    Func<T, Task> execute,
    Func<object, bool> canExecute = null,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
```

```csharp
public AsyncCommand(
    Func<T, Task> execute,
    Func<bool> canExecute,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
    : this(execute, _ => canExecute(), onException, continueOnCapturedContext, allowsMultipleExecutions)
```

### `AsyncCommand : IAsyncCommand`

```csharp
public AsyncCommand(
    Func<Task> execute,
    Func<object, bool> canExecute = null,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
```

```csharp
public AsyncCommand(
    Func<Task> execute,
    Func<bool> canExecute,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
    : this(execute, _ => canExecute(), onException, continueOnCapturedContext, allowsMultipleExecutions)
```

### `IAsyncCommand<TExecute, TCanExecute>`

```csharp
interface IAsyncCommand<TExecute, TCanExecute> : IAsyncCommand<TExecute>
```

### `IAsyncCommand<T>`

```csharp
interface IAsyncCommand<T> : ICommand
```

### `IAsyncCommand`

```csharp
interface IAsyncCommand : ICommand
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| ExecuteAsync() | Task | Executes the Command as a Task. |
| ExecuteAsync(T) | Task | Executes the Command as a Task. |
| ExecuteAsync(TExecute) | Task | Executes the Command as a Task. |

## Examples

### `AsyncCommand`

```csharp
class MyViewModel
{
    bool _isBusy;

    public MyViewModel()
    {
        ButtonCommand = new AsyncCommand(() => ExecuteButtonCommand(), _ => !IsBusy);
    }

    public IAsyncCommand ButtonCommand { get; }

    public bool IsBusy
    {
        get => _isBusy;
        set
        {
            if(_isBusy != value)
            {
                _isBusy = value;
                ButtonCommand.RaiseCanExecuteChanged();
            }
        }
    }    

    async Task ExecuteButtonCommand()
    {
        // ...
    }
}
```

### `AsyncCommand<T>`

```csharp
class MyViewModel
{
    bool _isBusy;

    public MyViewModel()
    {
        ButtonCommand = new AsyncCommand<int>(buttonClicks => ExecuteButtonCommand(buttonClicks), _ => !IsBusy);
    }

    public IAsyncCommand<int> ButtonCommand { get; }

    public bool IsBusy
    {
        get => _isBusy;
        set
        {
            if(_isBusy != value)
            {
                _isBusy = value;
                ButtonCommand.RaiseCanExecuteChanged();
            }
        }
    }   
    

    async Task ExecuteButtonCommand(int buttonClicks)
    {
        // ...
    }
}
```

### `AsyncCommand<TExecute, TCanExecute>`

```csharp
class MyViewModel
{
    public MyViewModel()
    {
        ButtonCommand = new AsyncCommand<int, bool>(buttonClicks => ExecuteButtonCommand(buttonClicks), isBusy => !isBusy);
    }

    public IAsyncCommand<int, bool> ButtonCommand { get; } 
    

    async Task ExecuteButtonCommand(int buttonClicks)
    {
        // ...
    }
}
```

## Sample project

[AboutViewModel](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/ViewModels/AboutViewModel.cs). 

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [AsyncCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/AsyncCommand.shared.cs)

## Related links

- [AsyncValueCommand](asyncvaluecommand.md)
