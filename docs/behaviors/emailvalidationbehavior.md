---
title: "Xamarin Community Toolkit EmailValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The EmailValidationBehavior allows users to determine whether or not a given text is a valid e-mail address."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit EmailValidationBehavior

The EmailValidationBehavior is a behavior that allows users to determine whether or not a given text value is a valid e-mail address. By adding this behavior to an `Entry` control it can be styled differently depending on whether a valid or an invalid e-mail address is provided. The validation is done through a regular expression which is used to verify whether or not the given value is a valid e-mail address. It can be overridden by the user to customize the validation through the properties it inherits from [ValidationBehavior](/xamarin-communitytoolkit/behaviors/validationbehavior).

## Syntax

```xml
<Entry Placeholder="Email">
    <Entry.Behaviors>
        <xct:EmailValidationBehavior DecorationFlags="Trim" InvalidStyle="{StaticResource InvalidEntryStyle}"/>
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| DefaultRegexPattern | string  | The regular expression used to verify whether or not the given value is a valid e-mail address. |


## Sample

- [EmailValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/EmailValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [EmailValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/EmailValidationBehavior.shared.cs)