---
title: "Xamarin Community Toolkit AsyncValueCommand"
author: brminnick
ms.author: bramin
description: "Allows for `ValueTask` to safely be used asynchronously with `ICommand`"
ms.date: 11/20/2020
---

# Xamarin Community Toolkit AsyncValueCommand

Allows for `ValueTask` to safely be used asynchronously with `ICommand`. 

If you're new to `ValueTask`, check out this great write-up: [Understanding the Whys, Whats, and Whens of ValueTask
](https://blogs.msdn.microsoft.com/dotnet/2018/11/07/understanding-the-whys-whats-and-whens-of-valuetask?WT.mc_id=mobile-0000-bramin).

## Syntax

```csharp
public AsyncValueCommand(Func<TExecute, ValueTask> execute,
                            Func<TCanExecute, bool>? canExecute = null,
                            Action<Exception>? onException = null,
                            bool continueOnCapturedContext = false) : IAsyncValueCommand<TExecute, ValueTask>
```

```csharp
public AsyncValueCommand(Func<T, ValueTask> execute,
                            Func<object?, bool>? canExecute = null,
                            Action<Exception>? onException = null,
                            bool continueOnCapturedContext = false) : IAsyncValueCommand<T>
```

```csharp
public AsyncValueCommand(Func<ValueTask> execute,
                            Func<object?, bool>? canExecute = null,
                            Action<Exception>? onException = null,
                            bool continueOnCapturedContext = false) : IAsyncValueCommand
```

```csharp
interface IAsyncValueCommand<TExecute, TCanExecute> : IAsyncValueCommand<TExecute>
```

```csharp
interface IAsyncValueCommand<T> : ICommand
```

```csharp
interface IAsyncValueCommand : ICommand`
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| ExecuteAsync(TExecute) | ValueTask | Executes the Command as a ValueTask |
| ExecuteAsync(T) | ValueTask | Executes the Command as a ValueTask |
| ExecuteAsync() | ValueTask | Executes the Command as a ValueTask |

## Examples

```csharp
public class ExampleClass
{
    bool _isBusy;

    public ExampleClass()
    {
        ExampleValueTaskCommand = new AsyncValueCommand(ExampleValueTaskMethod);
        ExampleValueTaskIntCommand = new AsyncValueCommand<int>(ExampleValueTaskMethodWithIntParameter);
        ExampleValueTaskIntCommandWithCanExecute = new AsyncValueCommand<int, int>(ExampleValueTaskMethodWithIntParameter, CanExecuteInt);
        ExampleValueTaskExceptionCommand = new AsyncValueCommand(ExampleValueTaskMethodWithException, onException: ex => Debug.WriteLine(ex.ToString()));
        ExampleValueTaskCommandWithCanExecuteChanged = new AsyncValueCommand(ExampleValueTaskMethod, _ => !IsBusy);
        ExampleValueTaskCommandReturningToTheCallingThread = new AsyncValueCommand(ExampleValueTaskMethod, continueOnCapturedContext: true);
    }

    public IAsyncValueCommand ExampleValueTaskCommand { get; }
    public IAsyncValueCommand<int> ExampleValueTaskIntCommand { get; }
    public IAsyncCommand<int, int> ExampleValueTaskIntCommandWithCanExecute { get; }
    public IAsyncValueCommand ExampleValueTaskExceptionCommand { get; }
    public IAsyncValueCommand ExampleValueTaskCommandWithCanExecuteChanged { get; }
    public IAsyncValueCommand ExampleValueTaskCommandReturningToTheCallingThread { get; }

    public bool IsBusy
    {
        get => _isBusy;
        set
        {
            if (_isBusy != value)
            {
                _isBusy = value;
                ExampleValueTaskCommandWithCanExecuteChanged.RaiseCanExecuteChanged();
            }
        }
    }

    async ValueTask ExampleValueTaskMethod()
    {
        var random = new Random();
        if (random.Next(10) > 9)
            await Task.Delay(1000);
    }

    async ValueTask ExampleValueTaskMethodWithIntParameter(int parameter)
    {
        var random = new Random();
        if (random.Next(10) > 9)
            await Task.Delay(parameter);
    }

    async ValueTask ExampleValueTaskMethodWithException()
    {
        var random = new Random();
        if (random.Next(10) > 9)
            await Task.Delay(1000);

        throw new Exception();
    }

    bool CanExecuteInt(int count)
    {
        if(count > 2)
            return true;
        
        return false;
    }

    void ExecuteCommands()
    {
        _isBusy = true;

        try
        {
            ExampleValueTaskCommand.Execute(null);
            ExampleValueTaskIntCommand.Execute(1000);
            ExampleValueTaskExceptionCommand.Execute(null);
            ExampleValueTaskCommandReturningToTheCallingThread.Execute(null);

            if (ExampleValueTaskCommandWithCanExecuteChanged.CanExecute(null))
                ExampleValueTaskCommandWithCanExecuteChanged.Execute(null);

            if(ExampleValueTaskIntCommandWithCanExecute.CanExecute(2))
                ExampleValueTaskIntCommandWithCanExecute.Execute(2);
        }
        finally
        {
            _isBusy = false;
        }
    }
}
```

## Sample project

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [AsyncValueCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/AsyncValueCommand.shared.cs)

## Related links

- [AsyncCommand](../asynccommand.md)
