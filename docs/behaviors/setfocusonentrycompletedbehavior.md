---
title: "Xamarin Community Toolkit SetFocusedOnEntryCompletedBehavior"
authors: jmegner, adenearnshaw
description: "The SetFocusedOnEntryCompletedBehavior allows a visual element to automatically gain focus once an entry has been completed."
ms.date: 03/03/2021
---

# Xamarin Community Toolkit SetFocusedOnEntryCompletedBehavior

The SetFocusedOnEntryCompletedBehavior is a behavior that gives focus to a specified visual element when an entry is completed.  For example, a page might have several entries in sequence, and it would be convenient to the user if completing an entry automatically switched focus to the next entry.

## Syntax

```xml
<StackLayout>
    <Entry x:Name="Entry1"
           Placeholder="Entry 1"
           xct:SetFocusOnEntryCompletedBehavior.NextElement="{x:Reference Entry2}"
           />
    <Entry x:Name="Entry2"
           Placeholder="Entry 2"
           xct:SetFocusOnEntryCompletedBehavior.NextElement="{x:Reference Entry3}"
           >
    </Entry>
    <Entry x:Name="Entry3"
           Placeholder="Entry 3 (no next entry this time)"
           />
</StackLayout>
```

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| NextElement | VisualElement | The `VisualElement` that should gain focus once the Entry is completed. |

## Sample

- [SetFocusedOnEntryCompletedBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Behaviors/SetFocusedOnEntryCompletedBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [SetFocusedOnEntryCompletedBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/AttachedBehaviors/SetFocusedOnEntryCompletedBehavior.shared.cs)
