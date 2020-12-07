---
title: "Xamarin Community Toolkit MultiValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The MultiValidationBehavior allows the user to combine multiple validators validating a given text depending on specified parameters."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit MultiValidationBehavior

The MultiValidationBehavior is a behavior that allows the user to combine multiple validators validating a given text depending on specified parameters. By adding this behavior to an `Entry` control it can be styled differently depending on whether a valid or an invalid text value is provided. By allowing the user to chain multiple existing validators together, it offers a high degree of customizability when it comes to validation. Additional properties handling validation are inherited from [ValidationBehavior](/xamarin-communitytoolkit/behaviors/validationbehavior).

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:MultiValidationBehavior 
            x:Name="MultiValidation"
            InvalidStyle="{StaticResource InvalidEntryStyle}">

            <xct:NumericValidationBehavior 
                xct:MultiValidationBehavior.Error="NaN" 
            />
            <xct:NumericValidationBehavior 
                MinimumValue="-10"
                xct:MultiValidationBehavior.Error="Min: -10" 
            />
            <xct:NumericValidationBehavior 
                MaximumValue="5"
                xct:MultiValidationBehavior.Error="Max: 5" 
            />

        </xct:MultiValidationBehavior>
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Error | object | An attached property on nested validators setting the error message for that validator. |
| Errors | `List<object>` | Holds the errors from all of the nested invalid validators. |

## Sample

- [MultiValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/MultiValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MultiValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/MultiValidationBehavior.shared.cs)