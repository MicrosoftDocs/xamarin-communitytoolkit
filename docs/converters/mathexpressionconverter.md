---
title: "Xamarin Community Toolkit MathExpressionConverter"
author: sattew
ms.author: joverslu
description: "The MathExpressionConverter allows users to calculate an expression at runtime."
ms.date: 04/01/2021
---

# Xamarin Community Toolkit MathExpressionConverter
![Pre-release API](~/images/pre-release.png)

The MathExpressionConverter is a converter that allows users to calculate an expression at runtime. All of binded arguments have notice: 
- **x** or **x0** — The first argument
- **x1** — The second argument
- ...
- **xN-1** — The N argument

> [!WARNING]
> Don't use the negative operations, constants or variables like "-cos(30)", "-x" or "-pi". This will return the error. Use multiplication by -1 instead.

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
| ^ | x ^ 5 | [Math.Pow](/dotnet/api/system.math.pow) |
| abs | abs(x) | [Math.Abs](/dotnet/api/system.math.abs#System_Math_Abs_System_Double_) |
| acos | acos(x) | [Math.Acos](https://docs.microsoft.com/dotnet/api/system.math.acos) |
| asin | asin(x) | [Math.Asin](https://docs.microsoft.com/dotnet/api/system.math.asin) |
| atan | atan(x) | [Math.Atan](https://docs.microsoft.com/dotnet/api/system.math.atan) |
| atan2 | atan2(x, 10) | [Math.Atan2](https://docs.microsoft.com/dotnet/api/system.math.atan2) |
| ceiling | ceiling(x) | [Math.Ceiling](https://docs.microsoft.com/dotnet/api/system.math.ceiling#System_Math_Ceiling_System_Double_) |
| cos | cos(x) | [Math.Cos](https://docs.microsoft.com/dotnet/api/system.math.cos) |
| cosh | cosh(x) | [Math.Cosh](https://docs.microsoft.com/dotnet/api/system.math.cosh) |
| exp | exp(x) | [Math.Exp](https://docs.microsoft.com/dotnet/api/system.math.exp) |
| floor | floor(x) | [Math.Floor](https://docs.microsoft.com/dotnet/api/system.math.floor#System_Math_Floor_System_Double_) |
| ieeeremainder | ieeeremainder(x, 16) | [Math.IEEERemainder](https://docs.microsoft.com/dotnet/api/system.math.ieeeremainder) |
| log | log(x, 17) | [Math.Log](https://docs.microsoft.com/dotnet/api/system.math.log#System_Math_Log_System_Double_System_Double_) |
| max | max(x, 18) | [Math.Max](https://docs.microsoft.com/dotnet/api/system.math.max#System_Math_Max_System_Double_System_Double_) |
| min | min(x, 19) | [Math.Min](https://docs.microsoft.com/dotnet/api/system.math.min#System_Math_Min_System_Double_System_Double_) |
| pow | round(x, 2) | [Math.Pow](https://docs.microsoft.com/dotnet/api/system.math.pow) |
| round | round(x, 1) | [Math.Round](https://docs.microsoft.com/dotnet/api/system.math.round#System_Math_Round_System_Double_System_Int32_) |
| sign | sign(x) | [Math.Sign](https://docs.microsoft.com/dotnet/api/system.math.sign#System_Math_Sign_System_Double_) |
| sin | sin(x) | [Math.Sin](https://docs.microsoft.com/dotnet/api/system.math.sin) |
| sinh | sinh(x) | [Math.Sinh](https://docs.microsoft.com/dotnet/api/system.math.sinh) |
| sqrt | sqrt(x) | [Math.Sqrt](https://docs.microsoft.com/dotnet/api/system.math.sqrt) |
| tan | tan(x) | [Math.Tan](https://docs.microsoft.com/dotnet/api/system.math.tan) |
| tanh | tanh(x) | [Math.Tanh](https://docs.microsoft.com/dotnet/api/system.math.tanh) |
| truncate | truncate(x) | [Math.Truncate](https://docs.microsoft.com/dotnet/api/system.math.truncate#System_Math_Truncate_System_Double_) |

## Constants
| Constant | Equivalent |
| -- | -- |
| e | [Math.E](https://docs.microsoft.com/dotnet/api/system.math.e) |
| pi | [Math.PI](https://docs.microsoft.com/dotnet/api/system.math.pi) |

## Sample

[MathExpressionConverter sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Converters/MathExpressionConverterPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [MathExpressionConverter source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/MathExpressionConverter/MathExpressionConverter.shared.cs)
* [MultiMathExpressionConverter.cs source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Converters/MathExpressionConverter/MultiMathExpressionConverter.shared.cs)
