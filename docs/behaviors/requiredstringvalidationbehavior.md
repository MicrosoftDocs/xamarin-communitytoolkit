---
title: "Xamarin Community Toolkit RequiredStringValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The RequiredStringValidationBehavior allows the user to determine if text input is equal to specific text."
ms.date: 12/08/2020
---

# Xamarin Community Toolkit RequiredStringValidationBehavior

The RequiredStringValidationBehavior is a behavior that allows the user to determine if text input is equal to specific text. For example, an `Entry` control can be styled differently depending on whether a valid or an invalid text input is provided. Additional properties handling validation are inherited from [ValidationBehavior](/xamarin-communitytoolkit/behaviors/validationbehavior).

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:RequiredStringValidationBehavior 
            InvalidStyle="{StaticResource InvalidEntryStyle}"
            RequiredString="OK"
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| RequiredString | string | The string that will be compared to the value provided by the user. |


## Sample

- [RequiredStringValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/RequiredStringValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [RequiredStringValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/RequiredStringValidationBehavior.shared.cs)
