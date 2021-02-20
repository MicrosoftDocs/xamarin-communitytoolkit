---
title: "Xamarin Community Toolkit LocalizedString"
author: maxkoshevoi
ms.author: v-makkos
description: "Allows users to handle multi-language support in C# code at runtime."
ms.date: 2/20/2021
---

# Xamarin Community Toolkit LocalizedString

The LocalizedString allows users to handle multi-language support in C# code at runtime. It uses the built-in [LocalizationResourceManager](../helpers/localizationresourcemanager.md) helper to react on current active [CultureInfo](xref:System.Globalization.CultureInfo) change.

## Examples

The following property raises `PropertyChanged` event and regenerates string using function provided in constructor, when `LocalizationResourceManager.Current.PropertyChanged` is triggered. 
As a result page will be updated with the value localized using new culture.

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
> For this example to work, you also need to update `AppResources.Culture` when `LocalizationResourceManager.Current.CurrentCulture` is changed. 
> Add this line above `LocalizationResourceManager.Current.Init()` call to do that.
> ```csharp
> LocalizationResourceManager.Current.PropertyChanged += (_, _) => AppResources.Culture >= LocalizationResourceManager.Current.CurrentCulture;
> ```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| Localized | string | Returns string localized using current culture. |

## Events

| Events | Description |
| -- | -- |
| PropertyChanged | Notifies of culture change. |

## Sample project

[Settings sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/ViewModels/SettingViewModel.cs)

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/samples/XCT.Sample).

## API

- [LocalizedString](https://github.com/xamarin/XamarinCommunityToolkit/blob/develop/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/LocalizedString.shared.cs)

## Related links

- [LocalizationResourceManager](../helpers/localizationresourcemanager.md)
- [TranslateExtension](../extensions/translateextension.md)