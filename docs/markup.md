---
title: "Xamarin Community Toolkit C# Markup"
author: VincentH-Net
description: "C# Markup is a set of fluent helper methods and classes to simplify the process of building declarative Xamarin.Forms user interfaces in C#."
ms.author: joverslu
ms.date: 12/07/2020
---

# Xamarin Community Toolkit C# Markup

[![Download Sample](media/shared/download.png) Download Xamarin.CommunityToolkit.MarkupSample](https://github.com/xamarin/XamarinCommunityToolkit)

C# Markup is a set of fluent helper methods and classes to simplify the process of building declarative Xamarin.Forms user interfaces in C#. The fluent API provided by C# Markup is available in the `Xamarin.CommunityToolkit.Markup` namespace.

Just as with XAML, C# Markup enables a clean separation between UI markup and UI logic. This can be achieved by separating UI markup and UI logic into distinct partial class files. For example, for a login page the UI markup would be in a file named *LoginPage.cs*, while the UI logic would be in a file named *LoginPage.logic.cs*.

The latest version of C# Markup requires **Xamarin.Forms 5** and is available in the [Xamarin.CommunityToolkit.Markup NuGet package](https://www.nuget.org/packages/Xamarin.CommunityToolkit.Markup).

C# Markup is available on all platforms supported by Xamarin.Forms.

> [!NOTE]
> The preview version of C# Markup is available in Xamarin.Forms 4.6 through 4.8 as an experimental feature.
>
> To migrate from the C# Markup preview version to XCT C# Markup:
> 1. Update to Xamarin.Forms Forms 5.
> 1. Install the Xamarin.CommunityToolkit.Markup NuGet package.
> 1. Change all references to the `Xamarin.Forms.Markup` namespace to `Xamarin.CommunityToolkit.Markup`, and ensure you include `using Xamarin.Forms;` in your markup files.
> 1. Update `Font` helper calls where needed. `Font` now has `family` as it's first parameter instead of `size`. For example, replace `.Font(15)` with `.Font(size: 15)` or `.FontSize(15)`.

If you are already familiar with the preview version of C# Markup, see [Additional Functionality In Xamarin Community Toolkit](#additional-functionality-in-xamarin-community-toolkit) below.

## Basic example

The following example shows setting the page content to a new [`Grid`](xref:Xamarin.Forms.Grid) containing a [`Label`](xref:Xamarin.Forms.Label) and an [`Entry`](xref:Xamarin.Forms.Entry), in C#:

```csharp
Grid grid = new Grid();

Label label = new Label { Text = "Code: " };
grid.Children.Add(label, 0, 1);

Entry entry = new Entry
{
    Placeholder = "Enter number", Keyboard = Keyboard.Numeric, BackgroundColor = Color.AliceBlue, TextColor = Color.Black, FontSize = 15,
    HeightRequest = 44, Margin = fieldMargin
};
grid.Children.Add(entry, 0, 2);
Grid.SetColumnSpan(entry, 2);
entry.SetBinding(Entry.TextProperty, new Binding("RegistrationCode"));

Content = grid;
```

This example creates a [`Grid`](xref:Xamarin.Forms.Grid) object, with child [`Label`](xref:Xamarin.Forms.Label) and [`Entry`](xref:Xamarin.Forms.Entry) objects. The `Label` displays text, and the `Entry` data binds to the `RegistrationCode` property of the viewmodel. Each child view is set to appear in a specific row in the `Grid`, and the `Entry` spans all the columns in the `Grid`. In addition, the height of the `Entry` is set, along with its keyboard, colors, the font size of its text, and its `Margin`. Finally, the `Page.Content` property is set to the `Grid` object.

C# Markup enables this code to be re-written using its fluent API:

```csharp
Content = new Grid { Children = 
{
    new Label { Text = "Code:" }
               .Row (BodyRow.CodeHeader) .Column (BodyCol.Header),

    new Entry { Placeholder = "Enter number", Keyboard = Keyboard.Numeric, BackgroundColor = Color.AliceBlue, TextColor = Color.Black } .FontSize (15)
               .Row (BodyRow.CodeEntry) .ColumnSpan (All<BodyCol>()) .Margin (fieldMargin) .Height (44)
               .Bind (nameof(vm.RegistrationCode))
}}};
```

This example is identical to the previous example, but the C# Markup fluent API simplifies the process of building the UI in C#.


> [!NOTE]
> C# Markup includes extension methods that set specific view properties. These extension methods are not meant to replace all property setters. Instead, they are designed to improve code readability, and can be used in combination with property setters. It's recommended to always use an extension method when one exists for a property, but you can choose your preferred balance.

## Namespace usings

To use C# Markup, include the following `using` statements in your markup files:

```csharp
using Xamarin.Forms;
using Xamarin.CommunityToolkit.Markup;
```

If you design your markup for:

- LTR only: also include `using Xamarin.CommunityToolkit.Markup.LeftToRight;`
- RTL only: also include `using Xamarin.CommunityToolkit.Markup.RightToLeft;`
- Both LTR and RTL: do not include `LeftToRight` or `RightToLeft` namespaces

To work with `Grid` rows and columns, also include `using static Xamarin.CommunityToolkit.Markup.GridRowsColumns;`.

## Data binding

C# Markup includes a `Bind` extension method, along with overloads, that creates a data binding between a view bindable property and a specified property. The `Bind` method knows the default bindable property for the majority of the controls that are included in Xamarin.Forms. Therefore, it's typically not necessary to specify the target property when using this method. You can also register the default bindable property for additional controls:

```csharp
DefaultBindableProperties.Register(
  HoverButton.CommandProperty, 
  RadialGauge.ValueProperty
);
```

The `Bind` method can be used to bind to any bindable property:

```csharp
new Label { Text = "No data available" }
           .Bind (Label.IsVisibleProperty, nameof(vm.Empty))
```

In addition, the `BindCommand` extension method can bind to a control's default `Command` and `CommandParameter` properties in a single method call:

```csharp
new TextCell { Text = "Tap me" }
              .BindCommand (nameof(vm.TapCommand))
```

By default, the `CommandParameter` is bound to the binding context. You can also specify the binding path and source for the `Command` and the `CommandParameter` bindings:

```csharp
new TextCell { Text = "Tap Me" }
              .BindCommand (nameof(vm.TapCommand), vm, nameof(Item.Id))
```

In this example, the binding context is an `Item` instance, so you don't need to specify a source for the `Id` `CommandParameter` binding.

If you only need to bind to `Command`, you can pass `null` to the `parameterPath` argument of the `BindCommand` method. Alternatively, use the `Bind` method.

You can also register the default `Command` and `CommandParameter` properties for additional controls:

```csharp
DefaultBindableProperties.RegisterCommand(
    (CustomViewA.CommandProperty, CustomViewA.CommandParameterProperty),
    (CustomViewB.CommandProperty, CustomViewB.CommandParameterProperty)
);
```

Inline converter code can be passed into the `Bind` method with the `convert` and `convertBack` parameters:

```csharp
new Label { Text = "Tree" }
           .Bind (Label.MarginProperty, nameof(TreeNode.TreeDepth),
                  convert: (int depth) => new Thickness(depth * 20, 0, 0, 0))
```

Type-safe converter parameters are also supported:

```csharp
new Label { }
           .Bind (nameof(viewModel.Text),
                  convert: (string text, int repeat) => string.Concat(Enumerable.Repeat(text, repeat)))
```

In addition, converter code and instances can be re-used with the `FuncConverter` class:

```csharp
FuncConverter<int, Thickness> treeMarginConverter = new FuncConverter<int, Thickness>(depth => new Thickness(depth * 20, 0, 0, 0));
new Label { Text = "Tree" }
           .Bind (Label.MarginProperty, nameof(TreeNode.TreeDepth), converter: treeMarginConverter),
```

The `FuncConverter` class also supports `CultureInfo` objects:

```csharp
cultureAwareConverter = new FuncConverter<DateTimeOffset, string, int>(
    (date, daysToAdd, culture) => date.AddDays(daysToAdd).ToString(culture)
);
```

It's also possible to data bind to `Span` objects that are specified with the `FormattedText` property:

```csharp
new Label { } .FormattedText (
    new Span { Text = "Built with " },
    new Span { TextColor = Color.Blue, TextDecorations = TextDecorations.Underline }
              .BindTapGesture (nameof(vm.ContinueToCSharpForMarkupCommand))
              .Bind (nameof(vm.Title))
)
```

### Gesture recognizers

`Command` and `CommandParameter` properties can be data bound to `GestureElement` and `View` types using the `BindClickGesture`, `BindSwipeGesture`, and `BindTapGesture` extension methods:

```csharp
new Label { Text = "Tap Me" }
           .BindTapGesture (nameof(vm.TapCommand))
```

This example creates a gesture recognizer of the specified type, and adds it to the [`Label`](xref:Xamarin.Forms.Label). The `Bind*Gesture` extension methods offer the same parameters as the `BindCommand` extension methods. However, by default `Bind*Gesture` does not bind `CommandParameter`, while `BindCommand` does.

To initialize a gesture recognizer with parameters, use the `ClickGesture`, `PanGesture`, `PinchGesture`, `SwipeGesture`, and `TapGesture` extension methods:

```csharp
new Label { Text = "Tap Me" }
           .TapGesture (g => g.Bind(nameof(vm.DoubleTapCommand)).NumberOfTapsRequired = 2)
```

Since a gesture recognizer is a `BindableObject`, you can use the `Bind` and `BindCommand` extension methods when you initialize it. You can also initialize custom gesture recognizer types with the `Gesture<TGestureElement, TGestureRecognizer>` extension method.

## Layout

C# Markup includes a series of layout extension methods that support positioning views in layouts, and content in views:

| Type | Extension methods |
|---|---|
| `FlexLayout` | `AlignSelf`, `Basis`, `Grow`, `Menu`, `Order`, `Shrink` |
| `Grid` | `Row`, `Column`, `RowSpan`, `ColumnSpan` |
| `Label` | `TextLeft`, `TextCenterHorizontal`, `TextRight` <br/> `TextTop`, `TextCenterVertical`, `TextBottom` <br/> `TextCenter` |
| `IPaddingElement` (e.g. `Layout`) | `Padding`, `Paddings` |
| `LayoutOptions` | `Left`, `CenterHorizontal`, `FillHorizontal`, `Right` <br/> `LeftExpand`, `CenterExpandHorizontal`, `FillExpandHorizontal`, `RightExpand` <br /> `Top`, `Bottom`, `CenterVertical`, `FillVertical` <br /> `TopExpand`, `BottomExpand`, `CenterExpandVertical`, `FillExpandVertical` <br /> `Center`, `Fill`, `CenterExpand`, `FillExpand` |
| `View` | `Margin`, `Margins` |
| `VisualElement` | `Height`, `Width`, `MinHeight`, `MinWidth`, `Size`, `MinSize` |

### Left-to-right and right-to-left support

For C# Markup that is designed to support either left-to-right (LTR) or right-to-left (RTL) flow direction, the extension methods listed above offer the most intuitive set of names: `Left`, `Right`, `Top` and `Bottom`.

To make the correct set of left and right extension methods available, and in the process make explicit which flow direction the markup is designed for, include one of the following two `using` directives: `using Xamarin.CommunityToolkit.Markup.LeftToRight;`, or `using Xamarin.CommunityToolkit.Markup.RightToLeft;`.

For C# Markup that is designed to support both left-to-right and right-to-left flow direction, it's recommended to use the extension methods in the following table rather than either of the above namespaces:

| Type | Extension methods |
|---|---|
| `Label` | `TextStart`, `TextEnd` |
| `LayoutOptions` | `Start`, `End` <br/> `StartExpand`, `EndExpand` |

### Layout line convention

The recommended convention is to put all the layout extension methods for a view on a single line in the following order:

1. The row and column that contain the view.
1. Alignment within the row and column.
1. Margins around the view.
1. View size.
1. Padding within the view.
1. Content alignment within the padding.

The following code shows an example of this convention:

```csharp
new Label { }
           .Row (BodyRow.Prompt) .ColumnSpan (All<BodyCol>()) .FillExpandHorizontal () .CenterVertical () .Margin (fieldNameMargin) .TextCenterHorizontal () // Layout line
```

Consistently following the convention enables you to quickly read C# Markup and build a mental map of where the view content is located in the UI.

## Grid rows and columns

Enumerations can be used to define [`Grid`](xref:Xamarin.Forms.Grid) rows and columns, instead of using numbers. This offers the advantage that renumbering is not required when adding or removing rows or columns.

> [!IMPORTANT]
> Defining [`Grid`](xref:Xamarin.Forms.Grid) rows and columns using enumerations requires the following `using` directive: `using static Xamarin.CommunityToolkit.Markup.GridRowsColumns;`

The following code shows an example of how to define and consume [`Grid`](xref:Xamarin.Forms.Grid) rows and columns using enumerations:

```csharp
using Xamarin.Forms;
using Xamarin.CommunityToolkit.Markup;
using Xamarin.CommunityToolkit.Markup.LeftToRight;
using static Xamarin.CommunityToolkit.Markup.GridRowsColumns;
// ...

enum BodyRow { Prompt, CodeHeader, CodeEntry, Button }
enum BodyCol { FieldLabel, FieldValidation }

View Build() => new Grid
{
    RowDefinitions = Rows.Define(
        (BodyRow.Prompt    , 170 ),
        (BodyRow.CodeHeader, 75  ),
        (BodyRow.CodeEntry , Auto),
        (BodyRow.Button    , Auto)
    ),

    ColumnDefinitions = Columns.Define(
        (BodyCol.FieldLabel     , Stars(0.5)),
        (BodyCol.FieldValidation, Star)
    ),

    Children =
    {
        new Label { LineBreakMode = LineBreakMode.WordWrap } .FontSize (15) .Bold ()
                   .Row (BodyRow.Prompt) .ColumnSpan (All<BodyCol>()) .FillExpandHorizontal () .CenterVertical () .Margin (fieldNameMargin) .TextCenterHorizontal ()
                   .Bind (nameof(vm.RegistrationPrompt)),

        new Label { Text = "Registration code" } .Bold ()
                   .Row (BodyRow.CodeHeader) .Column(BodyCol.FieldLabel) .Bottom () .Margin (fieldNameMargin),

        new Label { } .Italic ()
                   .Row (BodyRow.CodeHeader) .Column (BodyCol.FieldValidation) .Right () .Bottom () .Margin (fieldNameMargin)
                   .Bind (nameof(vm.RegistrationCodeValidationMessage)),

        new Entry { Placeholder = "E.g. 123456", Keyboard = Keyboard.Numeric, BackgroundColor = Color.AliceBlue, TextColor = Color.Black } .FontSize (15)
                   .Row (BodyRow.CodeEntry) .ColumnSpan (All<BodyCol>()) .Margin (fieldMargin) .Height (44)
                   .Bind (nameof(vm.RegistrationCode), BindingMode.TwoWay),

        new Button { Text = "Verify" } .Style (FilledButton)
                    .Row (BodyRow.Button) .ColumnSpan (All<BodyCol>()) .FillExpandHorizontal () .Margin (PageMarginSize)
                    .Bind (Button.IsVisibleProperty, nameof(vm.CanVerifyRegistrationCode))
                    .Bind (nameof(vm.VerifyRegistrationCodeCommand)),
    }
};
```

In addition, you can concisely define rows and columns without enumerations:

```csharp
new Grid
{
    RowDefinitions = Rows.Define (Auto, Star, 20),
    ColumnDefinitions = Columns.Define (Auto, Star, 20, 40)
    // ...
}
```

## Fonts

Controls that implement `IFontElement` can call the `FontSize`, `Bold`, `Italic`, and `Font` extension methods to set the appearance of the text displayed by the control, e.g.:

- `Button`
- `DatePicker`
- `Editor`
- `Entry`
- `Label`
- `Picker`
- `SearchBar`
- `Span`
- `TimePicker`

## Effects

Effects can be attached to controls with the `Effects` extension method:

```csharp
new Button { Text = "Tap Me" }
            .Effects (new ButtonMixedCaps())
```

## Logic integration

The `Invoke` extension method can be used to execute code inline in your C# Markup:

```csharp
new ListView { } .Invoke (l => l.ItemTapped += OnListViewItemTapped)
```

In addition, you can use the `Assign` extension method to access a control from outside the UI markup (in the UI logic file):

```csharp
new ListView { } .Assign (out MyListView)
```

## Styles

The following example shows how to create implicit and explicit styles using C# Markup:

```csharp
using Xamarin.Forms;
using Xamarin.CommunityToolkit.Markup;

namespace CSharpForMarkupDemos
{
    public static class Styles
    {
        static Style<Button> buttons, filledButton;
        static Style<Label> labels;
        static Style<Span> link;

        #region Implicit styles

        public static ResourceDictionary Implicit => new ResourceDictionary { Buttons, Labels };

        public static Style<Button> Buttons => buttons ?? (buttons = new Style<Button>(
            (Button.HeightRequestProperty, 44),
            (Button.FontSizeProperty, 13),
            (Button.HorizontalOptionsProperty, LayoutOptions.Center),
            (Button.VerticalOptionsProperty, LayoutOptions.Center)
        ));

        public static Style<Label> Labels => labels ?? (labels = new Style<Label>(
            (Label.FontSizeProperty, 13),
            (Label.TextColorProperty, Color.Black)
        ));

        #endregion Implicit styles

        #region Explicit styles

        public static Style<Button> FilledButton => filledButton ?? (filledButton = new Style<Button>(
            (Button.TextColorProperty, Color.White),
            (Button.BackgroundColorProperty, Color.FromHex("#1976D2")),
            (Button.CornerRadiusProperty, 5)
        )).BasedOn(Buttons);

        public static Style<Span> Link => link ?? (link = new Style<Span>(
            (Span.TextColorProperty, Color.Blue),
            (Span.TextDecorationsProperty, TextDecorations.Underline)
        ));

        #endregion Explicit styles
    }
}
```

The implicit styles can be consumed by loading them into the application resource dictionary:

```csharp
public App()
{
    Resources = Styles.Implicit;
    // ...
}
```

Explicit styles can be consumed with the `Style` extension method.

```csharp
using static CSharpForMarkupExample.Styles;
// ...

new Button { Text = "Tap Me" } .Style (FilledButton),
```

> [!NOTE]
> In addition to the `Style` extension method, there are also `ApplyToDerivedTypes`, `BasedOn`, `Add`, and `CanCascade` extension methods.

Alternatively, you can create your own styling extension methods:

```csharp
public static TButton Filled<TButton>(this TButton button) where TButton : Button
{
    button.Buttons(); // Equivalent to Style .BasedOn (Buttons)
    button.TextColor = Color.White;
    button.BackgroundColor = Color.Red;
    return button;
}
```

The `Filled` extension method can then be consumed as follows:

```csharp
new Button { Text = "Tap Me" } .Filled ()
```

## Platform-specifics

The `Invoke` extension method can be used to apply platform-specifics. However, to avoid ambiguity errors, don't include `using` directives for the `Xamarin.Forms.PlatformConfiguration.*Specific` namespaces directly. Instead, create a namespace alias and consume the platform-specific via the alias:

```csharp
using Xamarin.Forms;
using Xamarin.CommunityToolkit.Markup;
using PciOS = Xamarin.Forms.PlatformConfiguration.iOSSpecific;
// ...

new ListView { } .Invoke (l => PciOS.ListView.SetGroupHeaderStyle(l, PciOS.GroupHeaderStyle.Grouped))
```

In addition, if you consume certain platform-specifics frequently you can create fluent extension methods for them in your own extensions class:

```csharp
public static T iOSGroupHeaderStyle<T>(this T listView, PciOS.GroupHeaderStyle style) where T : Forms.ListView
{
  PciOS.ListView.SetGroupHeaderStyle(listView, style);
  return listView;
}
```

The extension method can then be consumed as follows:

```csharp
new ListView { } .iOSGroupHeaderStyle(PciOS.GroupHeaderStyle.Grouped)
```

For more information about platform-specifics, see [Android platform features](/xamarin/xamarin-forms/platform/android/), [iOS platform features](/xamarin/xamarin-forms/platform/ios/), and [Windows platform features](/xamarin/xamarin-forms/platform/windows/).

## Recommended convention

A recommended order and grouping of properties and helper methods is:

- **Purpose**: any property or helper methods whose value identifies the control's purpose (e.g. `Text`, `Placeholder`, .`Assign`).
- **Other**: all properties or helper methods that are not layout or binding, on the same line or multiple lines.
- **Layout**: layout is ordered inwards: rows and columns, layout options, margin, size, padding, and content alignment.
- **Bind**: data binding is performed at the end of the method chain, with one bound property per line. If the *default* bindable property is bound, it should be at the end of the method chain.

The following code shows an example of following this convention:

```csharp
new Button { Text = "Verify" /* purpose */ } .Style (FilledButton) // other
            .Row (BodyRow.Button) .ColumnSpan (All<BodyCol>()) .FillExpandHorizontal () .Margin (10) // layout
            .Bind (Button.IsVisibleProperty, nameof(vm.CanVerifyRegistrationCode)) // bind
            .Bind (nameof(vm.VerifyRegistrationCodeCommand)), // bind default

new Label { }
           .Assign (out animatedMessageLabel) // purpose
           .Invoke (label => label.SizeChanged += MessageLabel_SizeChanged) // other
           .Row (BodyRow.Message) .ColumnSpan (All<BodyCol>()) // layout
           .Bind (nameof(vm.Message)), // bind default
```

Consistently applying this convention enables you to quickly scan your C# Markup and build a mental image of the UI layout.

## Additional functionality in Xamarin Community Toolkit

In the Xamarin Community Toolkit, C# Markup adds support for:

- `MultiBinding`
- `MultiConverter`
- `BindableLayout`
- `RelativeLayout`
- `DynamicResource`

## Multi-Binding helpers

New overloads of the `Bind` helper offer support for [multi-binding](/xamarin/xamarin-forms/app-fundamentals/data-binding/multibinding).

There are overloads that support 2, 3 or 4 bindings with a type-safe inline converter:

```CSharp
new Label { }
    .Bind (Label.TextProperty,
        new Binding (nameof(vm.Name)),
        new Binding (nameof(vm.Score)),
        ((string name, bool score) v) => $"{v.name} Score: { v.score }"
    )
```

The value for all bindings are passed in as a `ValueTuple` with type-safe members.

You can also pass in a type-safe converter parameter:

```CSharp
new Label { }
    .Bind (Label.TextProperty,
        new Binding (nameof(vm.Name)),
        new Binding (nameof(vm.Score)),
        ((string name, int Score) v, bool winner) => $"{v.name} Score: { v.Score } Winner: { winner }",
        converterParameter: true
    )
```

Here `bool winner` gets the value from the `converterParameter`.

You can specify two-way conversion inline:

```CSharp
new Entry { }
    .Bind(Entry.TextProperty,
        new Binding (nameof(vm.Emoticon)),
        new Binding (nameof(vm.Repeat)),
        ((char emoticon, int repeat) v) => new string(v.emoticon, v.repeat),
        (string emoticons) => (emoticons[0], emoticons.Length)
    );
```

In the `convertBack` function you return the same `ValueTuple` that you receive in the `convert` function.
 
You can specify more than 4 bindings by passing in a multi-value converter:

```CSharp
new Label { }
    .Bind(Label.TextProperty,
        new List<BindingBase> {
            new Binding(nameof(vm.Name)),
            new Binding(nameof(vm.Score))
        },
        new FuncMultiConverter<string, bool>(
            (object[] values, bool winner) => $"{values[0]} Score: { values[1] } Winner: { winner }"
        )
    )
```

This is not type-safe: you will need to cast the values to their type in the `convert` function.

The `FuncMultiConverter` classes implement `IMultiValueConverter`. The class used for any number of bindings is `FuncMultiConverter<TDest, TParam>`, which only specifies the destination type and the parameter type of the convertor. The binding values are passed as an `object[]`.

There are also type-safe generic overloads for `FuncMultiConverter` that take 2, 3 or 4 values (and optionally a convertor parameter). These classes pass the binding values in a type-safe `ValueTuple`.

## Bindable layout helpers

The `EmptyView`, `EmptyViewTemplate`, `ItemsSource`, `ItemTemplate` and `ItemTemplateSelector` helpers offer support for [bindable layouts](/xamarin/xamarin-forms/user-interface/layouts/bindable-layouts) on all `Layout<View>` types:

```CSharp
new StackLayout { } 
    .ItemTemplate (() =>
        new Label { }
            .Bind (nameof(Item.Name))
        )
    .ItemsSource (vm.Items)
```

## RelativeLayout helpers

The `Children` helpers lets you add constrained child views to a `RelativeLayout`.

To create constrained views from normal views, four helpers have been added: `Unconstrained`, `Constraints` and two `Constrain` overloads. Each overload returns a corresponding `*ConstrainedView` class, which offers a fluent API for setting constraints on `RelativeLayout` child views.

Constraints on a child view can be set with:

- A single Bounds expression.
- Separate expressions for X, Y, Width and Height.
- Separate `Constraint` instances for X, Y, Width and Height. Each of these Constraint instances has overloads for:
  - Constant.
  - Relative to parent.
  - Relative to view.

The following code shows examples of using these helpers:

```CSharp
new RelativeLayout { } .Children (
    new Label { } // Bounds constrained
        .Assign (out Label child0)
        .Constrain(() => new Rectangle(30, 20, layout.Height / 2, layout.Height / 4)),

    new Label { } // Expressions constrained
        .Constrain() .X      (() => 30)
                     .Y      (() => 20)
                     .Width  (() => layout.Height / 2)
                     .Height (() => layout.Height / 4),

    new Label { } // Constraints constrained - parent relative
        .Constraints() .X      (30)
                       .Y      (20)
                       .Width  (parent => parent.Height / 5)
                       .Height (parent => parent.Height / 10),

    new Label { } // Constraints constrained - view relative
        .Constraints() .X      (child0, (layout, view) => view.Bounds.Right + 10)
                       .Y      (child0, (layout, view) => view.Y)
                       .Width  (child0, (layout, view) => view.Width)
                       .Height (child0, (layout, view) => view.Height),
) .Assign (out layout)
```

## Dynamic resource helpers

The `DynamicResource`, `DynamicResources` and `RemoveDynamicResources` helpers add support for setting dynamic resources on an `Element`:

```CSharp
new Label { }
    .DynamicResource (Label.TextProperty, "TextKey")

new Label { }
    .DynamicResources((Label.TextProperty     , "TextKey"),
                      (Label.TextColorProperty, "ColorKey"));
```

## Related links

- [Xamarin Community Toolkit](https://github.com/xamarin/XamarinCommunityToolkit)
- [Xamarin Forms Android platform features](/xamarin/xamarin-forms/platform/android/)
- [Xamarin Forms iOS platform features](/xamarin/xamarin-forms/platform/ios/)
- [Xamarin Forms Windows platform features](/xamarin/xamarin-forms/platform/windows/)
