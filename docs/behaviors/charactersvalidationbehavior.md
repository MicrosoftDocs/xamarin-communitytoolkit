---
title: "Xamarin Community Toolkit CharactersValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The CharactersValidationBehavior allows the user to validate a text input depending on specified parameters."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit CharactersValidationBehavior

The CharactersValidationBehavior is a behavior that allows the user to validate text input depending on specified parameters. For example, an `Entry` control can be styled differently depending on whether a valid or an invalid text value is provided. This behavior includes built-in checks such as checking for a certain number of digits or alphanumeric characters. Additional properties handling validation are inherited from [ValidationBehavior](validationbehavior.md).

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:CharactersValidationBehavior
            InvalidStyle="{StaticResource InvalidEntryStyle}"
            CharacterType="Digit"
            MaximumCharacterCount="10"
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| CharacterType | CharacterType | Provides an enumerated value to use to set how to handle comparisons. |
| MaximumCharacterCount | int | The maximum length of the text input that's allowed. |
| MinimumCharacterCount | int | The minimum length of the text input that's allowed. |

## Sample

- [CharactersValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Behaviors/CharactersValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [CharactersValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/CharactersValidationBehavior.shared.cs)
