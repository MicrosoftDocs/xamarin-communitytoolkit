---
title: "Xamarin Community Toolkit NumericValidationBehavior"
author: AlexHedley
description: "The NumericValidationBehavior allows the user to determine if a given text is a valid numeric value."
ms.author: joverslu
ms.date: 10/09/2020
---

# Xamarin Community Toolkit NumericValidationBehavior

The `NumericValidationBehavior` enables the user to determine if a given text is a valid numeric value.

## Syntax

```xaml
<Entry.Behaviors>
    <behaviors:NumericValidationBehavior InvalidStyle="{StaticResource InvalidEntryStyle}"
                                         MinimumValue="1.0"
                                         MaximumValue="100.0"/>
</Entry.Behaviors>
```

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


## Sample project

[NumericValidationBehaviorPage](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Behaviors/NumericValidationBehaviorPage.xaml). You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [NumericValidationBehavior](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Behaviors/NumericValidationBehavior.shared.cs)
