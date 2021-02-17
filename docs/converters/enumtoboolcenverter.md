---
title: "Xamarin Community Toolkit EnumToBoolConverter"
author: webducer
ms.author: joverslu
description: "The EnumToBoolConverter allows users to retrieve convert an enum value into a boolean value."
ms.date: 17/02/2021
---

# Xamarin Community Toolkit IndexToArrayItemConverter

The EnumToBoolConverter is a converter that allows users to convert a `Enum` value binding to a `bool` value. The `Enum` value can be compared against the `TrueList` or against the `ConverterParameter`.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             xmlns:myEnum="MyLittleApp.Models"
             x:Class="MyLittleApp.MainPage">

    <ContentPage.Resources>
        <ResourceDictionary>
            <!-- Converter with TRUE list -->
            <xct:EnumToBoolConverter x:Key="OpenIssueConverter">
                <xct:EnumToBoolConverter.TrueValues>
                    <myEnum:MyStateEnum>New</myEnum:MyStateEnum>
                    <myEnum:MyStateEnum>InReview</myEnum:MyStateEnum>
                    <myEnum:MyStateEnum>Developing</myEnum:MyStateEnum>
                </xct:EnumToBoolConverter.TrueValues>
            </xct:EnumToBoolConverter>
            <xct:EnumToBoolConverter x:Key="ClosedIssueConverter">
                <xct:EnumToBoolConverter.TrueValues>
                    <myEnum:MyStateEnum>WantFix</myEnum:MyStateEnum>
                    <myEnum:MyStateEnum>Resolved</myEnum:MyStateEnum>
                </xct:EnumToBoolConverter.TrueValues>
            </xct:EnumToBoolConverter>
            <!-- Converter, that uses parameter -->
            <xct:EnumToBoolConverter x:Key="IssueStateConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <!-- Converter with TRUE list -->
        <Label IsVisible="{Binding IssueState, Converter={StaticResource OpenIssueConverter}}" />
        <Label IsVisible="{Binding IssueState, Converter={StaticResource ClosedIssueConverter}}" />
        <!-- Converter, that uses parameter -->
        <Label IsVisible="{Binding IssueState, Converter={StaticResource IssueStateConverter}, ConverterParameter={x:Static myEnum:MyStateEnum.WaitingForCustomer}}" />

    </StackLayout>
</ContentPage>
```

## Sample

> [!NOTE]
> Currently there's no sample available for this feature yet. Want to add one? We are open to [community contributions](https://github.com/xamarin/XamarinCommunityToolkit).

<!-- [IndexToArrayItemConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit). -->

## API

* [IndexToArrayItemConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/EnumToBoolConverter.shared.cs)
