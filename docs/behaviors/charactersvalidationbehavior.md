---
title: "Xamarin Community Toolkit CharactersValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The CharactersValidationBehavior allows the user to validate a given text depending on specified parameters."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit CharactersValidationBehavior

The CharactersValidationBehavior is a behavior that allows the user to validate a given text depending on specified parameters. By adding this behavior to an `Entry` control it can be styled differently depending on whether a valid or an invalid text value is provided. It offers various built-in checks such as checking for a certain amount of digits or alphanumeric characters. Additional properties handling validation are inherited from [ValidationBehavior](/xamarin-communitytoolkit/behaviors/validationbehavior).

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
| CharacterType | CharacterType | Provides enumerated value to use to set how to handle comparisons. |
| MaximumCharacterCount | int | The maximum amount of times of the value that will be allowed. |
| MinimumCharacterCount | int | The minimum length of the value that will be allowed. |

## Sample

- [CharactersValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/CharactersValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [CharactersValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/CharactersValidationBehavior.shared.cs)