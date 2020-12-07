---
title: "Xamarin Community Toolkit UriValidationBehavior"
author: sthewissen
ms.author: joverslu
description: "The UriValidationBehavior allows users to determine whether or not a given text is a valid URI."
ms.date: 12/07/2020
---

# Xamarin Community Toolkit UriValidationBehavior

The UriValidationBehavior is a behavior that allows users to determine whether or not a given text value is a valid URI. By adding this behavior to an `Entry` control it can be styled differently depending on whether a valid or an invalid URI is provided. Additional properties handling validation are inherited from [ValidationBehavior](/xamarin-communitytoolkit/behaviors/validationbehavior).

## Syntax

```xml
<Entry>
    <Entry.Behaviors>
        <xct:UriValidationBehavior 
            UriKind="Absolute"
            InvalidStyle="{StaticResource InvalidEntryStyle}"
        />
    </Entry.Behaviors>
</Entry>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| UriKind | [UriKind](xref:System.UriKind)  | Provides enumerated value to use to set how to handle different kinds of URIs. |


## Sample

- [UriValidationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit.Sample/Pages/Behaviors/UriValidationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [UriValidationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Validators/UriValidationBehavior.shared.cs)