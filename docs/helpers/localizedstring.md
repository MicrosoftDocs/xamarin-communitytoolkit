---
title: "Xamarin Community Toolkit LocalizedString"
author: maxkoshevoi
ms.author: joverslu
description: "The LocalizedString class enables users to respond to system culture changes in C# code at runtime."
ms.date: 2/20/2021
---

# Xamarin Community Toolkit LocalizedString

The `LocalizedString` class enables users to respond to system culture changes in C# code at runtime. It uses the built-in [LocalizationResourceManager](../helpers/localizationresourcemanager.md) helper class to react to changes in the active [CultureInfo](xref:System.Globalization.CultureInfo).

## Examples

The following code raises the `PropertyChanged` event and regenerates the string using function provided in constructor, when the `LocalizationResourceManager.Current.PropertyChanged` event is raised. As a result, the page will be updated with the localized value using the new culture.

ViewModel:
```csharp
public LocalizedString AppVersion { get; } = new(() => string.Format(AppResources.Version, AppInfo.VersionString));
```

Page:
```xaml
<Label Text="{Binding AppVersion.Localized}"/>
```

Output:
```
Version: 1.0.0
```

> [!NOTE]
> For this example to work, you also need to update `AppResources.Culture` when `LocalizationResourceManager.Current.CurrentCulture` changes. 
> To do this, add the following code above the `LocalizationResourceManager.Current.Init()` call:
> ```csharp
> LocalizationResourceManager.Current.PropertyChanged += (_, _) => AppResources.Culture >= LocalizationResourceManager.Current.CurrentCulture;
> ```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| Localized | string | Returns a localized string using the current culture. |

## Events

| Events | Description |
| -- | -- |
| PropertyChanged | Provides notification of a culture change. |

## Sample project

[Settings sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/ViewModels/SettingViewModel.cs)

You can see this class in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/samples/XCT.Sample).

## API

- [LocalizedString](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/LocalizedString.shared.cs)

## Related links

- [LocalizationResourceManager](../helpers/localizationresourcemanager.md)
- [TranslateExtension](../extensions/translateextension.md)
