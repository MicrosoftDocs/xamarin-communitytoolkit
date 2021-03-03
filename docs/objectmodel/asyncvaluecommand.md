---
title: "Xamarin Community Toolkit AsyncValueCommand"
author: brminnick
ms.author: bramin
description: "Enables the ValueTask type to safely be used asynchronously with an ICommand."
ms.date: 11/20/2020
---

# Xamarin Community Toolkit AsyncValueCommand

Enables the `ValueTask` type to safely be used asynchronously with an `ICommand`.

For more information about the `ValueTask` type, see [Understanding the Whys, Whats, and Whens of ValueTask
](https://blogs.msdn.microsoft.com/dotnet/2018/11/07/understanding-the-whys-whats-and-whens-of-valuetask?WT.mc_id=mobile-0000-bramin).

## Syntax

### `AsyncValueCommand<TExecute, TCanExecute> : IAsyncValueCommand<TExecute, TCanExecute>`

```csharp
public AsyncValueCommand(
    Func<TExecute, ValueTask> execute,
    Func<TCanExecute, bool> canExecute = null,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
```

### `AsyncValueCommand<T> : IAsyncValueCommand<T>`

```csharp
public AsyncValueCommand(
    Func<T, ValueTask> execute,
    Func<object, bool> canExecute = null,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
```

```csharp
public AsyncValueCommand(
    Func<T, ValueTask> execute,
    Func<bool> canExecute,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
    : this(execute, _ => canExecute(), onException, continueOnCapturedContext, allowsMultipleExecutions)
```

### `AsyncValueCommand : IAsyncValueCommand`

```csharp
public AsyncValueCommand(
    Func<Task> execute,
    Func<object, bool> canExecute = null,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
```

```csharp
public AsyncValueCommand(
    Func<Task> execute,
    Func<bool> canExecute,
    Action<Exception> onException = null,
    bool continueOnCapturedContext = false,
    bool allowsMultipleExecutions = true)
    : this(execute, _ => canExecute(), onException, continueOnCapturedContext, allowsMultipleExecutions)
```

### `IAsyncValueCommand<TExecute, TCanExecute>`

```csharp
interface IAsyncValueCommand<TExecute, TCanExecute> : IAsyncValueCommand<TExecute>
```

### `IAsyncValueCommand<T>`

```csharp
interface IAsyncValueCommand<T> : ICommand
```

### `IAsyncValueCommand`

```csharp
interface IAsyncValueCommand : ICommand
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| ExecuteAsync() | ValueTask | Executes the Command as a ValueTask. |
| ExecuteAsync(T) | ValueTask | Executes the Command as a ValueTask. |
| ExecuteAsync(TExecute) | ValueTask | Executes the Command as a ValueTask. |

## Examples

### `AsyncValueCommand`

```csharp
class MyViewModel
{
    bool _isBusy;

    public MyViewModel()
    {
        ButtonCommand = new AsyncValueCommand(() => ExecuteButtonCommand(), _ => !IsBusy);
    }

    public IAsyncValueCommand ButtonCommand { get; }

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

    async ValueTask ExecuteButtonCommand()
    {
        // ...
    }
}
```

### `AsyncValueCommand<T>`

```csharp
class MyViewModel
{
    bool _isBusy;

    public MyViewModel()
    {
        ButtonCommand = new AsyncValueCommand<int>(buttonClicks => ExecuteButtonCommand(buttonClicks), _ => !IsBusy);
    }

    public IAsyncValueCommand<int> ButtonCommand { get; }

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
    

    async ValueTask ExecuteButtonCommand(int buttonClicks)
    {
        // ...
    }
}
```

### `AsyncValueCommand<TExecute, TCanExecute>`

```csharp
class MyViewModel
{
    public MyViewModel()
    {
        ButtonCommand = new AsyncValueCommand<int, bool>(buttonClicks => ExecuteButtonCommand(buttonClicks), isBusy => !isBusy);
    }

    public IAsyncValueCommand<int, bool> ButtonCommand { get; } 
    

    async ValueTask ExecuteButtonCommand(int buttonClicks)
    {
        // ...
    }
}
```

## Sample project

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit).

## API

- [AsyncValueCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/AsyncValueCommand.shared.cs)

## Related links

- [AsyncValueCommand](AsyncValueCommand.md)

## Related video

> [!Video https://channel9.msdn.com/Shows/XamarinShow/Xamarin-Community-Toolkit-Awesome-AsyncCommand--AsyncValueCommand/player]