---
title: "Xamarin Community Toolkit ValidationBehavior"
author: AlexHedley
description: "."
ms.author: joverslu
ms.date: 10/09/2020
---

# Xamarin Community Toolkit ValidationBehavior

<!-- Describe your control -->

## Syntax

```xaml

```

```csharp

```

## Sample output

<!-- Image/Text can show the output of the control/helper -->

## Properties

| Property | Type | Description |
| -- | -- | -- |
| IsValidProperty | BindableProperty | *Description* |
| ValidStyleProperty | BindableProperty | *Description* |
| InvalidStyleProperty | BindableProperty | *Description* |
| FlagsProperty | BindableProperty | *Description* |
| ValueProperty | BindableProperty | *Description* |
| ValuePropertyNameProperty | BindableProperty | *Description* |
| ForceValidateCommandProperty | BindableProperty | *Description* |
<!-- | currentStatus | ValidationFlags | *Description* | -->
<!-- | isAttaching | bool | *Description* | -->
<!-- | defaultValueBinding | BindingBase | *Description* | -->
| IsValid | bool | *Description* |
| ValidStyle | Style | *Description* |
| InvalidStyle | Style | *Description* |
| Flags | ValidationFlags | *Description* |
| Value | object | *Description* |
| ValuePropertyName | string | *Description* |
| ForceValidateCommand | ICommand | *Description* |
| DefaultValuePropertyName | string | *Description* |
| DefaultForceValidateCommand | ICommand | *Description* |

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| ForceValidate() | void | *Description* |
| DecorateValue() | object | *Description* |
| Validate(object) | bool | *Description* |
| GetDefaultForceValidateCommand(BindableObject) | *Description* |
| GetDefaultValuePropertyName(BindableObject) | *Description* |
<!-- | UpdateState(bool) | *Description* | -->
<!-- | UpdateStyle() | *Description* | -->

## Events

| Events | Description |
| -- | -- |
| OnAttachedTo(View) | *Description* |
| OnDetachingFrom(View) | *Description* |
| OnViewPropertyChanged(object, PropertyChangedEventArgs) | *Description* |
| OnValidationPropertyChanged(BindableObject, object, object) | *Description* |
| OnValuePropertyChanged(BindableObject, object, object) | *Description* |
| OnValuePropertyNamePropertyChanged(BindableObject, object, object) | *Description* |
| OnValuePropertyChanged() | *Description* |
| OnValuePropertyNamePropertyChanged() | *Description* |

## Examples

<!-- All control/helper must at least have an example to show the use of Properties and Methods in your control/helper with the output -->

## Sample project

<!-- Link to the sample page in the Xamarin community toolkit sample app -->
<!-- [control/helper name sample page Source](sample-page-link). You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample). -->

## API

- [ValidationBehavior](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Behaviors/ValidationBehavior.shared.cs)

## Related links

<!-- Optional -->

<!-- - [Topic 1](link) -->
<!-- - [Topic 2](link) -->
