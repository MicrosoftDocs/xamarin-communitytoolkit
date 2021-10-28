---
title: "Xamarin Community Toolkit AnimationBehavior"
author: sthewissen
ms.author: joverslu
description: "The AnimationBehavior allows the user to add an animation when an event is raised."
ms.date: 12/08/2020
---

# Xamarin Community Toolkit AnimationBehavior

The AnimationBehavior is a behavior that allows the user to add an animation when an event is raised. It offers various built-in animations such as fade, flip and scale. These are exposed through an instance of the `AnimationBase` class. Additional properties handling an event are inherited from [EventToCommandBehavior](eventtocommandbehavior.md).

## Syntax

```xml
<Button Text="Fade Animation">
    <Button.Behaviors>
        <xct:AnimationBehavior EventName="Clicked">
            <xct:AnimationBehavior.AnimationType>
                <xct:FadeAnimation
                    Easing="{x:Static Easing.Linear}"
                    Duration="100"
                />
            </xct:AnimationBehavior.AnimationType>
        </xct:AnimationBehavior>
    </Button.Behaviors>
</Button>
```

## Animations
The AnimationBehavior exposes a rich set of [Animation types](animationtypes.md)

## Properties

|Property  |Type  |Description  |
|---------|---------|---------|
| AnimationType | AnimationBase | Provides an animation definition for the behavior to execute. |

## Sample

- [AnimationBehavior sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Behaviors/AnimationBehaviorPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).

## API

* [AnimationBehavior source code](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/src/CommunityToolkit/Xamarin.CommunityToolkit/Behaviors/Animations/AnimationBehavior.shared.cs)
