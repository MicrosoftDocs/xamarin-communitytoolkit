---
title: "Xamarin Community Toolkit AnimationTypes"
author: bijington
ms.author: joverslu
description: "The AnimationType allows the user to perform an animation."
ms.date: 10/28/2021
---

# Xamarin Community Toolkit AnimationTypes

These represent types of animations that can be either be attached to views through the [AnimationBehavior](animationbehavior.md) or created programmatically and simply executed.

There are 2 differing types:

## 1. Simple animation (AnimationBase)

Each animation has its own properties which can be set such as `Duration` and `Easing` which they inherit from `AnimationBase`. Each animation also exposes its own properties, depending on what kind of animation it is. They can be used in the following ways:

### Attached

These can all be hooked up to be triggered by an event by attaching an [AnimationBehavior](animationbehavior.md) to the control. The `Animate` method receives the View that the behavior is attached to as a parameter.

```xml
<xct:AnimationBehavior EventName="Clicked">
    <xct:AnimationBehavior.AnimationType>
        <xct:FadeAnimation
            Easing="{x:Static Easing.Linear}"
            Duration="100"
        />
    </xct:AnimationBehavior.AnimationType>
</xct:AnimationBehavior>
```

### Code behind

An animation can also be constructed from code behind and manually triggered.

```csharp
var fadeAnimation = FadeAnimation
{
    Easing = Easing.Linear,
    Duration = 100
};

await fadeAnimation.Animate(myView);
```

### Custom implementation

The user can also create custom animations by inheriting from `AnimationBase` and implementing the `Animate` method.

```csharp
public class FadeAnimation : AnimationBase
{
    public static readonly BindableProperty FadeProperty =
        BindableProperty.Create(nameof(Fade), typeof(double), typeof(AnimationBase), 0.3, BindingMode.TwoWay);

    public double Fade
    {
        get => (double)GetValue(FadeProperty);
        set => SetValue(FadeProperty, value);
    }

    protected override uint DefaultDuration { get; set; } = 300;

    public override async Task Animate(View? view)
    {
        if (view != null)
        {
            await view.FadeTo(Fade, Duration, Easing);
            await view.FadeTo(1, Duration, Easing);
        }
    }
}
```

## 2. Compound animation (CompoundAnimationBase)

`CompoundAnimationBase` animations allow for the same behavior as `AnimationBase` with the following extra possibilities:

1. ability to animate multiple views
2. ability to cancel the animation
3. ability to control repetition of the animation

### Attached

These can all be hooked up to be triggered by an event by attaching an [AnimationBehavior](animationbehavior.md) to the control. The `Animate` method receives the View that the behavior is attached to as a parameter.

```xml
<xct:AnimationBehavior EventName="Clicked">
    <xct:AnimationBehavior.AnimationType>
        <xct:RubberBandAnimation
            Easing="{x:Static Easing.Linear}"
            Duration="100" 
            IsRepeating="{Binding IsBusy}"
        />
    </xct:AnimationBehavior.AnimationType>
</xct:AnimationBehavior>
```

### Code behind

An animation can also be constructed from code behind and manually triggered.

```csharp
var cancelAnimationTokenSource = new CancellationTokenSource();

var animation = RubberBandAnimation
{
    Easing = Easing.Linear,
    Duration = 100
};

await animation.Animate(cancelAnimationTokenSource.Token, myView, myView2);

// Cancel when you wish to stop the animation:
cancelAnimationTokenSource.Cancel();
```

### Custom implementation

The user can also create custom animations by inheriting from `CompoundAnimationBase` and implementing the `CreateAnimation` method.

```csharp
public class RubberBandAnimation : CompoundAnimationBase
{
    protected override uint DefaultDuration { get; set; } = 1000;

    protected override Animation CreateAnimation(params View[] views) 
    {
        var animation = new Animation();

        foreach (var view in views)
        {
            animation.Add(0, 0.3, new Animation(v => view.ScaleX = v, 1, 1.25));
            animation.Add(0, 0.3, new Animation(v => view.ScaleY = v, 1, 0.75));

            animation.Add(0.3, 0.4, new Animation(v => view.ScaleX = v, 1.25, 0.75));
            animation.Add(0.3, 0.4, new Animation(v => view.ScaleY = v, 0.75, 1.25));

            animation.Add(0.4, 0.5, new Animation(v => view.ScaleX = v, 0.75, 1.15));
            animation.Add(0.4, 0.5, new Animation(v => view.ScaleY = v, 1.25, 0.85));

            animation.Add(0.5, 0.65, new Animation(v => view.ScaleX = v, 1.15, 0.95));
            animation.Add(0.5, 0.65, new Animation(v => view.ScaleY = v, 0.85, 1.05));

            animation.Add(0.65, 0.75, new Animation(v => view.ScaleX = v, 0.95, 1.05));
            animation.Add(0.65, 0.75, new Animation(v => view.ScaleY = v, 1.05, 0.95));

            animation.Add(0.75, 1, new Animation(v => view.ScaleX = v, 1.05, 1));
            animation.Add(0.75, 1, new Animation(v => view.ScaleY = v, 0.95, 1));
        }

        return animation;
    }
}
```

## Sample

- [Animations sample page Source](https://github.com/xamarin/XamarinCommunityToolkit/blob/main/samples/XCT.Sample/Pages/Animations/AnimationPage.xaml)

You can see this in action in the [Xamarin Community Toolkit Sample App](https://github.com/xamarin/XamarinCommunityToolkit).