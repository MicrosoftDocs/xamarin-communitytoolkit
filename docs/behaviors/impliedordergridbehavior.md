---
title: "Xamarin Community Toolkit ImpliedOrderGridBehavior"
description: "A behavior for a grid that assigns grid column and row assignments based on the order children are added to the grid."
author: bmacombe
ms.date: 10/22/2020
ms.topic: conceptual
ms.author: joverslu
ms.assetid: 3e9dced9-2d71-4092-be1f-8a3bf8172725
ms.prod: xamarin
---

# Xamarin Community Toolkit ImpliedOrderGridBehavior

The ImpliedOrderGridBehavior enables you to automatically assign a `Grid` row and column to a view based on the order the view is added to the `Grid`. You only need to setup the row and column definitions and then add children to the Grid. You may still assign `RowSpan` and `ColumnSpan` to views and their values will be taken into account when assigning a row and column to a view. If a view has a user defined row or column value it will be honored.

## Logging and exceptions

By default the behavior will log warnings for the following conditions:

- The number of children added to the Grid exceeds the number of available cells based on the row and column definitions.
- A child with a ColumnSpan value that exceeds the number of columns to it's right.
- A child with a RowSpan value that exceeds the number of rows below it.
- A child with a user assigned row and/or column is placed over an already placed child.

> [!NOTE]
> You may optionally set the `ThrowOnLayoutWarning` property to `true`, which will raise exceptions instead of warnings.

## Syntax

```xaml
<Grid x:Name="TestGrid" Margin="30" BackgroundColor="Gray">
    <Grid.Behaviors>
	<autoLayoutGrid:ImpliedOrderGridBehavior />
    </Grid.Behaviors>

    <Grid.RowDefinitions>
        <RowDefinition Height="*" />
        <RowDefinition Height="*" />
        <RowDefinition Height="*" />
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    <Grid .ColumnDefinitions>
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="*" />
    </Grid.ColumnDefinitions>

    <!-- Row 0 -->
    <autoLayoutGrid:TestLabel Grid .RowSpan="2"/>
    <autoLayoutGrid:TestLabel />
    <autoLayoutGrid:TestLabel />
    <autoLayoutGrid:TestLabel Grid .ColumnSpan="2"/>

    <!-- Row 1 -->
    <autoLayoutGrid:TestLabel/>
    <autoLayoutGrid:TestLabel />
    <autoLayoutGrid:TestLabel Grid .ColumnSpan="2"
                              Grid .RowSpan="2" />

    <!-- Row 2 -->
    <autoLayoutGrid:TestLabel />
    <autoLayoutGrid:TestLabel />
    <autoLayoutGrid:TestLabel />

    <!-- Row 3 -->
    <autoLayoutGrid:TestLabel />

</Grid >
```

![Example layout image](impliedgridorderbehavior-images/ImpliedOrderGridBehavior.png)

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
|ThrowOnLayoutWarning|bool|When true warnings will throw an exception instead of being logged. Defaults to false.|

## Sample

[ImpliedOrderGridBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkitSample/Pages/Behaviors/ImpliedOrderGridBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [ImpliedOrderGridBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/XamarinCommunityToolkit/Behaviors/ImpliedOrderGridBehavior.shared.cs)
