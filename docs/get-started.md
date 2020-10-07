---
title: "Getting Started with the Xamarin Community Toolkit"
author: AlexHedley
ms.author: joverslu
description: "Overview of how to get started with the Xamarin Community Toolkit to build amazing Xamarin.Forms apps."
---

# Getting Started with the Xamarin Community Toolkit

The toolkit is available as a NuGet package that can be added to any existing or new project using Visual Studio.

1. Open an existing project, or create a new project using the Blank Forms App template.

2. In the Solution Explorer panel, right click on your project name and select **Manage NuGet Packages**. Search for **Xamarin.CommunityToolkit**, and choose the desired NuGet Package from the list.

    ![NuGet Package](resources/images/managenuget.png "Manage NuGet Package Image")

3. There's no need to reference the toolkit in your XAML pages as we're sharing the namespace definition with Xamarin.Forms.

    * In your C# page, you can add the namespace to the toolkit:

        ```c#
        using Xamarin.CommunityToolkit;
        ```

4. Check out the rest of the documentation to learn more about implementing specific features. 

## Other Resources 

Download the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit) from the repository to see the controls in an actual app.

We recommend developers who are new to Xamarin.Forms to visit the [Get started with Xamarin](/xamarin/get-started/) documentation. 

Visit the [Xamarin Community Toolkit GitHub Repository](https://github.com/xamarin/XamarinCommunityToolkit) to see the current source code, what is coming next, and clone the repository.  Community contributions are welcome!
