---
title: "Xamarin Community Toolkit LocalizationResourceManager"
author: maxkoshevoi
ms.author: v-makkos
description: "Helper class to help user handle multi-language support at runtime."
ms.date: 2/20/2021
---

# Xamarin Community Toolkit LocalizationResourceManager

Helper class to help user handle multi-language support at runtime.
Intended to be used by [TranslateExtension](../extensions/translateextension.md)<!--"Uncomment when this class is released" and [LocalizedString](localizedstring.md)-->.

## Examples

### Initializing

Call `Init` in the `App` class constructor, and pass your resource manager to it. 
You can also subscribe to `PropertyChanged` to ensure that culture of your app resources is actual.

```csharp
LocalizationResourceManager.Current.PropertyChanged += (_, _) => AppResources.Culture = LocalizationResourceManager.Current.CurrentCulture;
LocalizationResourceManager.Current.Init(AppResources.ResourceManager);
```

### Changing Culture

Use `SetCulture` method to change the culture.

```csharp
LocalizationResourceManager.Current.SetCulture(newCulture);
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| CurrentCulture | [CultureInfo](xref:System.Globalization.CultureInfo) | Culture used to provide resource values. |

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| Init(ResourceManager) | void | Initializes LocalizationResourceManager. |
| Init(ResourceManager, CultureInfo) | void | Initializes LocalizationResourceManager. |
| SetCulture(CultureInfo) | void | Sets new culture. |
| GetValue(string) | string | Retrieves localized resource value based on `CurrentCulture`. |
| Invalidate() | void | Rises `PropertyChanged` event. |

## Events

| Events | Description |
| -- | -- |
| PropertyChanged | Notifies of culture change. |

## Sample project

[App class Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/App.xaml.cs)
[Settings sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/ViewModels/SettingViewModel.cs)

You can see this element in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/XamarinCommunityToolkitSample).

## API

- [LocalizationResourceManager](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/LocalizationResourceManager.shared.cs)

## Related links

- [TranslateExtension](../extensions/translateextension.md)
<!-- Uncomment when this class is released - [LocalizedString](localizedstring.md)-->