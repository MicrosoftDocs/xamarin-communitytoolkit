---
title: "Xamarin Community Toolkit MaskedBehavior"
author: sthewissen
ms.author: joverslu
description: "The MaskedBehavior allows the user to define an input mask for data entry."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit MaskedBehavior

The MaskedBehavior is a behavior that allows the user to define an input mask for data entry. By adding this behavior to an `Entry` control it will force the user to only input values matching a given mask. Popular examples of its usage include input of a credit card number or a phone number.

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:MaskedBehavior 
            Mask="AA-AA-AA" 
            UnMaskedCharacter="A"
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| Mask | string | The mask that the input value needs to match. |
| UnMaskedCharacter | string | The placeholder character for when no input has been given yet. |


## Sample

- [MaskedBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/MaskedBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MaskedBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/MaskedBehavior.shared.cs)