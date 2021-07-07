---
title: "Xamarin Community Toolkit MathExpressionConverter"
author: sattew
ms.author: joverslu
description: "The MathExpressionConverter allows users to calculate an expression at runtime."
ms.date: 04/01/2021
---

# Xamarin Community Toolkit MathExpressionConverter

![Pre-release API.](~/images/pre-release.png)

The `MathExpressionConverter`is a converter that allows users to calculate an expression at runtime from supplied arguments:

- **x** or **x0** — The first argument
- **x1** — The second argument
- ...
- **xN-1** — The N argument

> [!WARNING]
> Avoid negative operations, constants or variables such as "-cos(30)", "-x" or "-pi", which will return an error. Instead, use multiplication by -1.

## Syntax

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">
    <ContentPage.Resources>
         <ResourceDictionary>
             <xct:MathExpressionConverter x:Key="MathExpressionConverter" />
             <xct:MultiMathExpressionConverter x:Key="MultiMathExpressionConverter" />
         </ResourceDictionary>
    </ContentPage.Resources>

    <StackLayout>

        <Frame
           x:Name="CalculatedFrame"
           HeightRequest="120"
           CornerRadius="{Binding Source={x:Reference CalculatedFrame}, Path=HeightRequest, Converter={StaticResource MathExpressionConverter}, ConverterParameter='x/2'}">

        <Label TextColor="Black">
            <Label.Text>
                <MultiBinding Converter="{StaticResource MultiMathExpressionConverter}"
                              ConverterParameter="x0 * x1"
                              StringFormat="The area of Frame = {0}">
                    <Binding Path="{Binding Source={x:Reference CalculatedFrame}, Path=HeightRequest}" />
                    <Binding Path="{Binding Source={x:Reference CalculatedFrame}, Path=WidthRequest}" />
                </MultiBinding>
            </Label.Text>
        </Label>

    </StackLayout>
</ContentPage>
```

## Operations

| Operation | Example | Equivalent |
| -- | -- | -- |
| + | x + 1 | — |
| - | x - 2 | — |
| * | x * -3 | — |
| / | x / 4 | — |
| ^ | x ^ 5 | [Math.Pow](xref:System.Math.Pow*) |
| abs | abs(x) | [Math.Abs](xref:System.Math.Abs*) |
| acos | acos(x) | [Math.Acos](xref:System.Math.Acos*) |
| asin | asin(x) | [Math.Asin](xref:System.Math.Asin*) |
| atan | atan(x) | [Math.Atan](xref:System.Math.Atan*) |
| atan2 | atan2(x, 10) | [Math.Atan2](xref:System.Math.Atan2*) |
| ceiling | ceiling(x) | [Math.Ceiling](xref:System.Math.Ceiling*) |
| cos | cos(x) | [Math.Cos](xref:System.Math.Cos*) |
| cosh | cosh(x) | [Math.Cosh](xref:System.Math.Cosh*) |
| exp | exp(x) | [Math.Exp](xref:System.Math.Exp*) |
| floor | floor(x) | [Math.Floor](xref:System.Math.Floor*) |
| ieeeremainder | ieeeremainder(x, 16) | [Math.IEEERemainder](xref:System.Math.IEEERemainder*) |
| log | log(x, 17) | [Math.Log](xref:System.Math.Log*) |
| max | max(x, 18) | [Math.Max](xref:System.Math.Max*) |
| min | min(x, 19) | [Math.Min](xref:System.Math.Min*) |
| pow | round(x, 2) | [Math.Pow](xref:System.Math.Pow*) |
| round | round(x, 1) | [Math.Round](xref:System.Math.Round*) |
| sign | sign(x) | [Math.Sign](xref:System.Math.Sign*) |
| sin | sin(x) | [Math.Sin](xref:System.Math.Sin*) |
| sinh | sinh(x) | [Math.Sinh](xref:System.Math.Sinh*) |
| sqrt | sqrt(x) | [Math.Sqrt](xref:System.Math.Sqrt*) |
| tan | tan(x) | [Math.Tan](xref:System.Math.Tan*) |
| tanh | tanh(x) | [Math.Tanh](xref:System.Math.Tanh*) |
| truncate | truncate(x) | [Math.Truncate](xref:System.Math.Truncate*) |

## Constants

| Constant | Equivalent |
| -- | -- |
| e | [Math.E](xref:System.Math.E) |
| pi | [Math.PI](xref:System.Math.PI) |

## Sample

[MathExpressionConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/MathExpressionConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MathExpressionConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/MathExpressionConverter/MathExpressionConverter.shared.cs)
* [MultiMathExpressionConverter.cs source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/MathExpressionConverter/MultiMathExpressionConverter.shared.cs)
