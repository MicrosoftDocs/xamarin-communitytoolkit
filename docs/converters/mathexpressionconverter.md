---
title: "Xamarin Community Toolkit MathExpressionConverter"
author: sattew
ms.author: joverslu
description: "The MathExpressionConverter allows users to calculate an expression at runtime."
ms.date: 04/01/2021
---

# Xamarin Community Toolkit MathExpressionConverter
![Pre-release API](~/images/pre-release.png)

The `MathExpressionConverter`is a converter that allows users to calculate an expression at runtime. All of the binded arguments have notice: 

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
| ^ | x ^ 5 | [Math.Pow](xref:System.Math.Pow) |
| abs | abs(x) | [Math.Abs](xref:System.Math.abs#System_Math_Abs_System_Double_) |
| acos | acos(x) | [Math.Acos](xref:System.Math.Acos) |
| asin | asin(x) | [Math.Asin](xref:System.Math.Asin) |
| atan | atan(x) | [Math.Atan](xref:System.Math.Atan) |
| atan2 | atan2(x, 10) | [Math.Atan2](xref:System.Math.Atan2) |
| ceiling | ceiling(x) | [Math.Ceiling](xref:System.Math.Ceiling#System_Math_Ceiling_System_Double_) |
| cos | cos(x) | [Math.Cos](xref:System.Math.Cos) |
| cosh | cosh(x) | [Math.Cosh](xref:System.Math.Cosh) |
| exp | exp(x) | [Math.Exp](xref:System.Math.Exp) |
| floor | floor(x) | [Math.Floor](xref:System.Math.Floor#System_Math_Floor_System_Double_) |
| ieeeremainder | ieeeremainder(x, 16) | [Math.IEEERemainder](xref:System.Math.ieeeremainder) |
| log | log(x, 17) | [Math.Log](xref:System.Math.Log#System_Math_Log_System_Double_System_Double_) |
| max | max(x, 18) | [Math.Max](xref:System.Math.Max#System_Math_Max_System_Double_System_Double_) |
| min | min(x, 19) | [Math.Min](xref:System.Math.Min#System_Math_Min_System_Double_System_Double_) |
| pow | round(x, 2) | [Math.Pow](xref:System.Math.Pow) |
| round | round(x, 1) | [Math.Round](xref:System.Math.Round#System_Math_Round_System_Double_System_Int32_) |
| sign | sign(x) | [Math.Sign](xref:System.Math.Sign#System_Math_Sign_System_Double_) |
| sin | sin(x) | [Math.Sin](xref:System.Math.Sin) |
| sinh | sinh(x) | [Math.Sinh](xref:System.Math.Sinh) |
| sqrt | sqrt(x) | [Math.Sqrt](xref:System.Math.Sqrt) |
| tan | tan(x) | [Math.Tan](xref:System.Math.Tan) |
| tanh | tanh(x) | [Math.Tanh](xref:System.Math.Tanh) |
| truncate | truncate(x) | [Math.Truncate](xref:System.Math.Truncate#System_Math_Truncate_System_Double_) |

## Constants

| Constant | Equivalent |
| -- | -- |
| e | [Math.E](xref:System.Math.E) |
| pi | [Math.PI](xref:System.Math.Pi) |

## Sample

[MathExpressionConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/MathExpressionConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MathExpressionConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/MathExpressionConverter/MathExpressionConverter.shared.cs)
* [MultiMathExpressionConverter.cs source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/MathExpressionConverter/MultiMathExpressionConverter.shared.cs)
