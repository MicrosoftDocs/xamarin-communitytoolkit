---
title: "Xamarin Community Toolkit NumericValidationBehavior"
author: AlexHedley
description: "."
ms.author: joverslu
ms.date: 10/09/2020
---

# Xamarin Community Toolkit Numeric Validation Behavior

<!-- Describe your control -->

## Syntax

```xaml
<Entry.Behaviors>
    <behaviors:NumericValidationBehavior InvalidStyle="{StaticResource InvalidEntryStyle}"
                                         MinimumValue="1.0"
                                         MaximumValue="100.0"/>
</Entry.Behaviors>
```

```csharp

```

## Sample output

<!-- Image/Text can show the output of the control/helper -->

## Properties

| Property | Type | Description |
| -- | -- | -- |
| MinimumValue | double | *Description* |
| MaximumValue | double | *Description* |

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| Validate(object) | bool | *Description* |
| B(float, string) | int | Description |

## Events

| Events | Description |
| -- | -- |

## Examples

<!-- All control/helper must at least have an example to show the use of Properties and Methods in your control/helper with the output -->

## Sample project

[NumericValidationBehaviorPage](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Behaviors/NumericValidationBehaviorPage.xaml). You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [NumericValidationBehavior](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Behaviors/NumericValidationBehavior.shared.cs)
