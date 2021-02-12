---
title: "Xamarin Community Toolkit ValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The ValidationBehavior allows users to create custom validation behaviors."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit ValidationBehavior

The ValidationBehavior allows users to create custom validation behaviors. All of the validation behaviors in the Xamarin Community Toolkit inherit from this behavior, to expose a number of shared properties. Users can inherit from this class to create a custom validation behavior currently not supported through the Xamarin Community Toolkit.

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| ForceValidateCommand | [ICommand](xref:System.Windows.Input.ICommand) | Allows the user to provide a custom ICommand that handles forcing validation. This is a bindable property. |
| Flags | ValidationFlags | Provides an enumerated value that specifies how to handle validation. This is a bindable property. |
| InvalidStyle | [Style](xref:Xamarin.Forms.Style) | The Style to apply to the element when validation fails. This is a bindable property. |
| IsNotValid | bool  | Indicates whether or not the current value is considered invalid. This is a bindable property. |
| IsValid | bool  | Indicates whether or not the current value is considered valid. This is a bindable property. |
| ValidStyle | [Style](xref:Xamarin.Forms.Style) | The Style to apply to the element when validation is successful.  |
| Value | object | The value to validate. This is a bindable property. |
| ValuePropertyName | string | Allows the user to override the property that will be used as the value to validate. This is a bindable property. |

## Sample

> [!WARNING]
> This class should not be used without inheriting from it. Therefore, there is no sample available.

## API

* [ValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/ValidationBehavior.shared.cs)
