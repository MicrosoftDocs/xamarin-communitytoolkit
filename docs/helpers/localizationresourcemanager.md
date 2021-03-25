---
title: "Xamarin Community Toolkit LocalizationResourceManager"
author: maxkoshevoi
ms.author: joverslu
description: "The Xamarin Community Toolkit LocalizationResourceManager helper class enables users to respond to culture changes at runtime."
ms.date: 2/20/2021
---

# Xamarin Community Toolkit LocalizationResourceManager

The `LocalizationResourceManager` class is a helper class that enables users to respond to culture changes at runtime. This class is typically used by the [`TranslateExtension`](../extensions/translateextension.md) class and [`LocalizedString`](localizedstring.md).

## Examples

The following sections show examples of how to use the `LocalizationResourceManager` class.

### Initialization

Call the `Init` method in your `App` class constructor, and pass your resource manager to it:

```csharp
LocalizationResourceManager.Current.PropertyChanged += (_, _) => AppResources.Culture = LocalizationResourceManager.Current.CurrentCulture;
LocalizationResourceManager.Current.Init(AppResources.ResourceManager);
```

You can also subscribe to the `PropertyChanged` event to ensure that your app responds to system culture changes.

### Change culture

Use the `CurrentCulture` property to change the culture:

```csharp
LocalizationResourceManager.Current.CurrentCulture = newCulture;
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| CurrentCulture | [CultureInfo](xref:System.Globalization.CultureInfo) | The culture used to provide resource values. |

## Methods

| Methods | Return Type | Description |
| -- | -- | -- |
| Init(ResourceManager) | void | Initializes a LocalizationResourceManager. |
| Init(ResourceManager, CultureInfo) | void | Initializes a LocalizationResourceManager. |
| GetValue(string) | string | Retrieves the localized resource value based on `CurrentCulture`. |

## Events

| Events | Description |
| -- | -- |
| PropertyChanged | Provides notification of a culture change. |

## Sample project

[App class Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/App.xaml.cs)
[Settings sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/ViewModels/SettingViewModel.cs)

You can see this class in action in the [Xamarin community toolkit sample app](https://github.com/xamarin/XamarinCommunityToolkit/tree/main/samples/XCT.Sample).

## API

- [LocalizationResourceManager](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Helpers/LocalizationResourceManager.shared.cs)

## Related links

- [TranslateExtension](../extensions/translateextension.md)
- [LocalizedString](localizedstring.md)
