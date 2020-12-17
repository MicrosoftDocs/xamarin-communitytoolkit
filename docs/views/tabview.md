---
title: "Xamarin Community Toolkit TabView"
description: "The TabView control allows the user to display a set of tabs and their respective content."
author: jfversluis
ms.author: joverslu
ms.date: 12/17/2020
---

# Xamarin Community Toolkit TabView

The `TabView` control allows the user to display a set of tabs and their respective content. Other than the native tab bars, the `TabView` is fully customizable.

## Syntax

Underneath you can see a simple example of a `TabView` implementation.

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:xct="http://xamarin.com/schemas/2020/toolkit"
             x:Class="MyLittleApp.MainPage">

     <Grid>
        <xct:TabView
                TabStripPlacement="Bottom"
                TabStripBackgroundColor="Blue"
                TabStripHeight="60"
                TabIndicatorColor="Yellow"
                TabContentBackgroundColor="Yellow">

                <xct:TabViewItem
                    Icon="triangle.png"
                    Text="Tab 1"
                    TextColor="White"
                    TextColorSelected="Yellow"
                    FontSize="12">
                    <Grid 
                        BackgroundColor="Gray">
                        <Label
                            HorizontalOptions="Center"
                            VerticalOptions="Center"
                            Text="TabContent1" />
                    </Grid>
                </xct:TabViewItem>

                <xct:TabViewItem
                    Icon="circle.png"
                    Text="Tab 2"
                    TextColor="White"
                    TextColorSelected="Yellow"
                    FontSize="12">
                    <Grid>
                        <Label    
                            HorizontalOptions="Center"
                            VerticalOptions="Center"
                            Text="TabContent2" />
                    </Grid>
                </xct:TabViewItem>
        </xct:TabView>
  </Grid>

</ContentPage>
```

## Properties

The following properties are available on the `TabView` object:

|Property  |Type  |Description  |
|---------|---------|---------|
| TabItemsSource |  IEnumerable | A collection used to generate the TabView's tab items.   |
| TabViewItemDataTemplate |  DataTemplate | the template the Tab View uses to generate tab items' header.   |
| TabContentDataTemplate |  DataTemplate | The template the Tab View uses to generate tab items' content.  |
| SelectedIndex |  Int | Gets or sets the currently selected tab. Default is 0.   |
| TabStripPlacement |    TabStripPlacement   |  The TabStrip placement (top or bottom).  |
| TabStripBackground | Brush | The TabStrip background.  |
| TabIndicatorBrush | Brush | The TabIndicator background.  |
| TabIndicatorHeight | double | The TabIndicator height.  |
| TabIndicatorWidth | double | The TabIndicator width.  |
| TabIndicatorPlacement | TabIndicatorPlacement |   |
| TabIndicatorView | View |  The TabIndicator content. |
| TabContentBackground | Brush | The tab content background.  |
| TabContentHeight | Double | The tab content height.  |
| TabStripHeight | Double | The TabStrip height.  |
| TabContentHeight | Double | The tab content height.  |
| IsTabTransitionEnabled | Bool | Enable or disable the transition between tabs.  |
| IsSwipeEnabled | Bool | Enable or disable the swipe gesture.   |

The following properties are available on the `TabViewItem` object:

|Property  |Type  |Description  |
|---------|---------|---------|
| Text |  string | The text of the tab.   |
| TextColor | [`Color`](xref:Xamarin.Forms.Color) | The text color of the tab.   |
| TextColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The text color of the selected tab.   |
| FontSize | FontSize |  The font size used in the tab text. |
| FontSizeSelected | FontSize | The font size used in the selected tab.   |
| FontFamily | string | The font family  used in the tab.  |
| FontFamilySelected | string | The font family used in the selected tab.  |
| FontAttributes | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | The font attributes used in the tab.  |
| FontAttributesSelected | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | The font attributes used in the selected tab.   |
| Icon | [`ImageSource`](xref:Xamarin.Forms.ImageSource) | The icon of the tab.   |
| IconSelected | [`ImageSource`](xref:Xamarin.Forms.ImageSource) | The ImageSource used as icon in the selected tab.   |
| Content | View | The content of the tab. Is View, can use anything as content.   |
| BadgeText | bool | The badge text used in the tab.  |
| BadgeTextColor | [`Color`](xref:Xamarin.Forms.Color) | The badge text color used in the tab.   |
| BadgeTextColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The badge text color used in the selected tab.   |
| BadgeBackgroundColor | [`Color`](xref:Xamarin.Forms.Color) | The badge color used in the tab.   |
| BadgeBackgroundColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The badge color used in the selected tab.   |
| IsSelected | bool | a bool that indicate if the tab is selected or not.  |
| TapCommand | [`ICommand`](xref:System.Windows.Input.ICommand) | Command that is executed when the user tap a tab.   |
| TapCommandParameter | object | The tap command parameter.   |

## Events

The following event are available on the `TabView` object:

| Event  |Type  |Description  |
|---------|---------|---------|
| SelectionChanged | EventHandler | Event that is raised when the selected tab changed.   |
| Scrolled | EventHandler | Event that is raised when is swiping between tabs.  |

The following event are available on the `TabViewItem` object:

| Event  |Type  |Description  |
|---------|---------|---------|
| TabTapped | EventHandler | Event that is raised when the user tap a tab.   |

## Sample

[TabView Sample Source](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/samples/XCT.Sample/Pages/Views/TabView)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

- [TabView source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/TabView/TabView.shared.cs)

- [TabViewItem source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/TabView/TabViewItem.shared.cs)
