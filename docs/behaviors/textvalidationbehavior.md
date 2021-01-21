---
title: "Xamarin Community Toolkit TextValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The TextValidationBehavior allows the user to validate a given text depending on specified parameters."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit TextValidationBehavior

The TextValidationBehavior is a behavior that allows the user to validate a given text depending on specified parameters. By adding this behavior to an `Entry` control it can be styled differently depending on whether a valid or an invalid text value is provided. It offers various built-in checks such as checking for a certain length or whether or not the input value matches a specific regular expression. Additional properties handling validation are inherited from [ValidationBehavior](validationbehavior.md).

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:TextValidationBehavior
            InvalidStyle="{StaticResource InvalidEntryStyle}"
            MinimumLength="1"
            MaximumLength="10"
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| DecorationFlags | TextDecorationFlags | Provides enumerated value to use to set how to handle white spaces. |
| MaximumLength | int | The maximum length of the value that will be allowed. |
| MinimumLength | int | The minimum length of the value that will be allowed. |
| RegexOptions | [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) | Provides enumerated values to use to set regular expression options. |
| RegexPattern | string | The regular expression pattern which the value will have to match before it will be allowed. |

## Sample

- [TextValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Behaviors/TextValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [TextValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/TextValidationBehavior.shared.cs)
