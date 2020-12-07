---
title: "Xamarin Community Toolkit EmailValidationBehavior"
author: AlexHedley
description: "The EmailValidationBehavior allows users to determine whether or not a given text is a valid e-mail address."
ms.author: joverslu
ms.date: 10/09/2020
---

# Xamarin Community Toolkit EmailValidationBehavior

The `EmailValidationBehavior` enables users to determine whether or not a given text is a valid e-mail address.

## Syntax

```xaml
<Entry Placeholder="Email">
    <Entry.Behaviors>
        <behaviors:EmailValidationBehavior DecorationFlags="Trim" InvalidStyle="{StaticResource InvalidEntryStyle}"/>
    </Entry.Behaviors>
</Entry>
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| DefaultRegexPattern | string  | *Description* |

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| DecorateValue | object  | *Description* |

## Sample project

[EmailValidationBehaviorPage](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Behaviors/EmailValidationBehaviorPage.xaml). You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [EmailValidationBehavior](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Behaviors/EmailValidationBehavior.shared.cs)
