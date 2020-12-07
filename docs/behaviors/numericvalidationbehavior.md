---
title: "Xamarin Community Toolkit NumericValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The NumericValidationBehavior allows the user to determine if a given text is a valid numeric value."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit NumericValidationBehavior

The NumericValidationBehavior is a behavior that allows the user to determine if a given text is a valid numeric value. By adding this behavior to an `Entry` control it can be styled differently depending on whether a valid or an invalid numeric value is provided. Additional properties handling validation are inherited from [ValidationBehavior](/xamarin-communitytoolkit/behaviors/validationbehavior).

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:NumericValidationBehavior 
            InvalidStyle="{StaticResource InvalidEntryStyle}"
            MinimumValue="1.0"
            MaximumValue="100.0"
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| MaximumDecimalPlaces | int | The maximum number of decimal places that will be allowed. |
| MaximumValue | double | The maximum numeric value that will be allowed. |
| MinimumDecimalPlaces | int | The minimum number of decimal places that will be allowed. |
| MinimumValue | double | The minimum numeric value that will be allowed. |


## Sample

- [NumericValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/NumericValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [NumericValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/NumericValidationBehavior.shared.cs)