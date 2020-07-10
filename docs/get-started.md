---
title: "Get Started with Xamarin Community Toolkit"
author: AlexHedley
description: "Xamarin Community Toolkit provides a single cross-platform API that works with any iOS, Android, or UWP application that can be accessed from shared code no matter how the user interface is created."
---

# Get started with Xamarin.CommunityToolkit

Xamarin.CommunityToolkit provides a single cross-platform API that works with any iOS, Android, or UWP application that can be accessed from shared code no matter how the user interface is created. <!--See the [platform & feature support guide](platform-feature-support.md) for more information on supported operating systems.-->

## Installation

Xamarin.CommunityToolkit is available as a NuGet package. It can be added to any existing project using Visual Studio with the follow steps:

1. Download and install [Visual Studio](https://visualstudio.microsoft.com/) with the [Visual Studio tools for Xamarin](/xamarin/get-started/installation/).

2. Open an existing project, or create a new project using the Blank App template under **Visual Studio C#** (Android, iPhone & iPad, or Cross-Platform).

    > [!IMPORTANT]
    > If adding to a UWP project ensure Build 16299 or higher is set in the project properties.

3. Add the [**Xamarin.CommunityToolkit**](https://www.nuget.org/packages/Xamarin.CommunityToolkit/) NuGet package to each project:

    <!--markdownlint-disable MD023 -->
    # [Visual Studio](#tab/windows)

    In the Solution Explorer panel, right click on the solution name and select **Manage NuGet Packages**. Search for **Xamarin.CommunityToolkit** and install the package into **ALL** projects including Android, iOS, UWP, and .NET Standard libraries.

    # [Visual Studio for Mac](#tab/macos)

    In the Solution Explorer panel, right click on the project name and select **Add > Add NuGet Packages...**. Search for **Xamarin.CommunityToolkit** and install the package into **ALL** projects including Android, iOS, and .NET Standard libraries.

    -----

4. Add a reference to Xamarin.CommunityToolkit in any C# class to reference the APIs.

    ```csharp
    using XamarinCommunityToolkit;
    ```

<!--
5. Xamarin.CommunityToolkit requires platform-specific setup:

    # [Android](#tab/android)

    No additional setup required.

    # [iOS](#tab/ios)

    No additional setup required.

    # [UWP](#tab/uwp)

    No additional setup required.

    -----
-->

5. Follow the [Xamarin.CommunityToolkit guides](index.md) that enable you to copy and paste code snippets for each feature.

## Other resources

We recommend developers new to Xamarin visit [Getting started with Xamarin development](/xamarin/get-started/).

Visit the [Xamarin.CommunityToolkit GitHub Repository](https://github.com/xamarin/XamarinCommunityToolkit) to see the current source code, what is coming next, run samples, and clone the repository. Community contributions are welcome!

<!--
Browse through the [API documentation](xref:Xamarin.CommunityToolkit) for every feature of Xamarin.CommunityToolkit.
-->
