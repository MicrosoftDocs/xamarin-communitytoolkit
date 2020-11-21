---
title: "Xamarin Community Toolkit AsyncCommand"
author: brminnick
ms.author: bramin
description: "Allows for `Task` to safely be used asynchronously with `ICommand`"
ms.date: 11/20/2020
---

# Xamarin Community Toolkit AsyncCommand

Allows for `Task` to safely be used asynchronously with `ICommand`.

## Syntax

```csharp
public AsyncCommand(Func<TExecute, Task> execute,
                     Func<TCanExecute, bool>? canExecute = null,
                     Action<Exception>? onException = null,
                     bool continueOnCapturedContext = false) : IAsyncCommand<TExecute, TCanExecute>
```

```csharp
public AsyncCommand(Func<T, Task> execute,
                     Func<object?, bool>? canExecute = null,
                     Action<Exception>? onException = null,
                     bool continueOnCapturedContext = false) : IAsyncCommand<T>`
```

```csharp
public AsyncCommand(Func<Task> execute,
                     Func<object?, bool>? canExecute = null,
                     Action<Exception>? onException = null,
                     bool continueOnCapturedContext = false) : IAsyncCommand
```

```csharp
interface IAsyncCommand<TExecute, TCanExecute> : IAsyncCommand<TExecute>
```

```csharp
interface IAsyncCommand<T> : ICommand
```

```csharp
interface IAsyncCommand : ICommand
```

```csharp
interface IAsyncCommand : ICommand
```

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| ExecuteAsync(TExecute) | Task | Executes the Command as a Task |
| ExecuteAsync(T) | Task | Executes the Command as a Task |
| ExecuteAsync() | Task | Executes the Command as a Task |

## Examples

```csharp
public class ExampleClass
{
    bool _isBusy;

    public ExampleClass()
    {
        ExampleAsyncCommand = new AsyncCommand(ExampleAsyncMethod);
        ExampleAsyncIntCommand = new AsyncCommand<int>(ExampleAsyncMethodWithIntParameter);
        ExampleAsyncIntCommandWithCanExecute = new AsyncCommand<int, int>(ExampleAsyncMethodWithIntParameter, CanExecuteInt);
        ExampleAsyncExceptionCommand = new AsyncCommand(ExampleAsyncMethodWithException, onException: ex => Console.WriteLine(ex.ToString()));
        ExampleAsyncCommandWithCanExecuteChanged = new AsyncCommand(ExampleAsyncMethod, _ => !IsBusy);
        ExampleAsyncCommandReturningToTheCallingThread = new AsyncCommand(ExampleAsyncMethod, continueOnCapturedContext: true);
    }

    public IAsyncCommand ExampleAsyncCommand { get; }
    public IAsyncCommand<int> ExampleAsyncIntCommand { get; }
    public IAsyncCommand<int, int> ExampleAsyncIntCommandWithCanExecute { get; }
    public IAsyncCommand ExampleAsyncExceptionCommand { get; }
    public IAsyncCommand ExampleAsyncCommandWithCanExecuteChanged { get; }
    public IAsyncCommand ExampleAsyncCommandReturningToTheCallingThread { get; }
    
    public bool IsBusy
    {
        get => _isBusy;
        set
        {
            if (_isBusy != value)
            {
                _isBusy = value;
                ExampleAsyncCommandWithCanExecuteChanged.RaiseCanExecuteChanged();
            }
        }
    }

    async Task ExampleAsyncMethod()
    {
        await Task.Delay(1000);
    }
  
    async Task ExampleAsyncMethodWithIntParameter(int parameter)
    {
        await Task.Delay(parameter);
    }

    async Task ExampleAsyncMethodWithException()
    {
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
            ExampleAsyncCommand.Execute(null);
            ExampleAsyncIntCommand.Execute(1000);
            ExampleAsyncExceptionCommand.Execute(null);
            ExampleAsyncCommandReturningToTheCallingThread.Execute(null);
            
            if(ExampleAsyncCommandWithCanExecuteChanged.CanExecute(null))
                ExampleAsyncCommandWithCanExecuteChanged.Execute(null);
            
            if(ExampleAsyncIntCommandWithCanExecute.CanExecute(1))
                ExampleAsyncIntCommandWithCanExecute.Execute(1);
        }
        finally
        {
            _isBusy = false;
        }
    }
}
```

## Sample project

[AboutViewModel](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/ViewModels/AboutViewModel.cs). 

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [AsyncCommand](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/ObjectModel/AsyncCommand.shared.cs)

## Related links

- [AsyncValueCommand](./asyncvaluecommand.md)