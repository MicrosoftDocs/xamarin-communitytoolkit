---
title: "Xamarin Community Toolkit TabView"
description: "The TabView control allows the user to display a set of tabs and their content."
author: jfversluis
ms.author: joverslu
ms.date: 12/17/2020
---

# Xamarin Community Toolkit TabView

The `TabView` control allows the user to display a set of tabs and their content. The `TabView` is fully customizable, other than the native tab bars.

## Syntax

The following code shows a simple example of a `TabView` implementation:

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
| IsSwipeEnabled | bool | Enable or disable the swipe gesture.   |
| IsTabTransitionEnabled | bool | Enable or disable the transition between tabs.  |
| SelectedIndex |  int | Gets or sets the currently selected tab. Default is 0.   |
| TabContentBackgroundColor | [`Color`](xref:Xamarin.Forms.Color) | The tab content background.  |
| TabContentDataTemplate | [`DataTemplate`](xref:Xamarin.Forms.DataTemplate) | The template the TabView uses to generate tab items' content.  |
| TabContentHeight | double | The tab content height.  |
| TabIndicatorColor | [`Color`](xref:Xamarin.Forms.Color) | The TabIndicator background.  |
| TabIndicatorHeight | double | The TabIndicator height.  |
| TabIndicatorPlacement | TabIndicatorPlacement | The selected tab indicator placement (top, center or bottom). |
| TabIndicatorView | [`View`](xref:Xamarin.Forms.View) |  The TabIndicator content. |
| TabIndicatorWidth | double | The TabIndicator width.  |
| TabItems | ObservableCollection&lt;TabViewItem&gt; | Property that reflects the current tab items. |
| TabItemsSource |  `IList` | A collection used to generate the TabView's tab items.   |
| TabStripPlacement |  TabStripPlacement |  The TabStrip placement (top or bottom).  |
| TabStripBackgroundColor | [`Color`](xref:Xamarin.Forms.Color) | The `Color` of the TabStrip background. This can't be used with `TabStripBackgroundView`. |
| TabStripBackgroundView | [`View`](xref:Xamarin.Forms.View) | The `View` representing the TabStrip background. This can't be used with `TabStripBackgroundColor`. |
| TabStripHeight | double | The TabStrip height.  |
| TabViewItemDataTemplate |  [`DataTemplate`](xref:Xamarin.Forms.DataTemplate) | The template the TabView uses to generate tab items' header. |

The following properties are available on the `TabViewItem` object:

|Property  |Type  |Description  |
|---------|---------|---------|
| BadgeBackgroundColor | [`Color`](xref:Xamarin.Forms.Color) | The badge color used in the tab.   |
| BadgeBackgroundColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The badge color used in the selected tab.   |
| BadgeBorderColor | [`Color`](xref:Xamarin.Forms.Color) | The badge border color used in the tab.   |
| BadgeBorderColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The badge border color used in the selected tab.   |
| BadgeText | string | The badge text used in the tab.  |
| BadgeTextColor | [`Color`](xref:Xamarin.Forms.Color) | The badge text color used in the tab.   |
| BadgeTextColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The badge text color used in the selected tab.   |
| Content | [`View`](xref:Xamarin.Forms.View) | The content of the tab. Anything can be used as content.   |
| CurrentBadgeBackgroundColor | [`Color`](xref:Xamarin.Forms.Color) | Read-only property that reflects the currently used `BadgeBackgroundColor` |
| CurrentBadgeBorderColor | [`Color`](xref:Xamarin.Forms.Color) | Read-only property that reflects the currently used `BadgeBorderColor` |
| CurrentContent | [`View`](xref:Xamarin.Forms.View) | Read-only property that reflects the currently used `Content` |
| CurrentFontAttributes | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | Read-only property that reflects the currently used `FontAttributes` |
| CurrentFontFamily | string | Read-only property that reflects the currently used `FontFamily` |
| CurrentFontSize | double | Read-only property that reflects the currently used `FontSize` |
| CurrentIcon | [`ImageSource`](xref:Xamarin.Forms.ImageSource) | Read-only property that reflects the currently used `Icon` |
| CurrentTextColor | [`Color`](xref:Xamarin.Forms.Color) | Read-only property that reflects the currently used `TextColor` |
| FontAttributes | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | The font attributes used in the tab.  |
| FontAttributesSelected | [`FontAttributes`](xref:Xamarin.Forms.FontAttributes) | The font attributes used in the selected tab.   |
| FontFamily | string | The font family used in the tab.  |
| FontFamilySelected | string | The font family used in the selected tab.  |
| FontSize | double |  The font size used in the tab text. |
| FontSizeSelected | double | The font size used in the selected tab. |
| Icon | [`ImageSource`](xref:Xamarin.Forms.ImageSource) | The icon of the tab.   |
| IconSelected | [`ImageSource`](xref:Xamarin.Forms.ImageSource) | The ImageSource used as icon in the selected tab.   |
| IsSelected | bool | A bool that indicates if the tab is selected or not.  |
| TabAnimation | ITabViewItemAnimation | The transition animation of a tab. |
| TabWidth | double | The width of a tab item |
| TapCommand | [`ICommand`](xref:System.Windows.Input.ICommand) | Command that is executed when the user taps a tab.   |
| TapCommandParameter | object | The tap command parameter.   |
| Text | string | The tab text. |
| TextColor | [`Color`](xref:Xamarin.Forms.Color) | The text color of the tab.   |
| TextColorSelected | [`Color`](xref:Xamarin.Forms.Color) | The text color of the selected tab. |

## Events

The following events are available on the `TabView` object:

| Event  |Type  |Description  |
|---------|---------|---------|
| SelectionChanged | TabSelectionChangedEventHandler | Event that is raised when the selected tab changed.   |
| Scrolled | TabViewScrolledEventHandler | Event that is raised when swiping between tabs.  |

The following events are available on the `TabViewItem` object:

| Event  |Type  |Description  |
|---------|---------|---------|
| TabTapped | TabTappedEventHandler | Event that is raised when the user tap a tab.   |

## Sample

[TabView Sample Source](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/samples/XCT.Sample/Pages/Views/TabView)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

- [TabView source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/TabView/TabView.shared.cs)

- [TabViewItem source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Views/TabView/TabViewItem.shared.cs)

## Related video

> [!Video https://channel9.msdn.com/Shows/XamarinShow/Xamarin-Community-Toolkit-TabView/player]
