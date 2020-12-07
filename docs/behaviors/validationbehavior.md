---
title: "Xamarin Community Toolkit ValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The ValidationBehavior allows users to create custom validation behaviors."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit ValidationBehavior

The ValidationBehavior allows users to create custom validation behaviors. All of the validation related behaviors in the Xamarin Community Toolkit inherit from this behavior to expose a number of shared properties. Users can inherit from this class to create a custom validation behavior currently not supported through the Xamarin Community Toolkit.

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| ForceValidateCommand | [ICommand](xref:System.Windows.Input.ICommand) | |
| Flags | ValidationFlags | |
| InvalidStyle | [Style](xref:Xamarin.Forms.Style) | |
| IsValid | bool  |  |
| ValidStyle | [Style](xref:Xamarin.Forms.Style) | |
| Value | object | |
| ValuePropertyName | string | |


## Sample

> [!NOTE]
> This class should not be used without inheriting from it. Therefore, there is no sample available.

## API

* [ValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/ValidationBehavior.shared.cs)