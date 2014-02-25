View animations are a simple way to use the more powerful Core Animation framework. Historically, view animations are configured by creating animation transactions using class methods. However, current best practice is to use the block-based view animation APIs.

### Animatable view properties

The following view properties may be animated:

- Frame
- Bounds
- Center
- Background Color
- Alpha
- Transform

### Basic animation

To set up a basic animation, specify the initial value of the property that you want to animate, then specify the ending value in the animation block. For example, the snippet below is used to fade in a view.

```
// Set the start value of the property
view.alpha = 0;
[UIView animateWithDuration:2 animations:^{
   // Set the end state
}];
```

### Chaining animations

You can chain animations by adding additional animations in the completion block. For example, in the snippet below, a view is faded in, pauses for 1 second, then fades back out.

```
view.alpha = 0;
[UIView animateWithDuration:2 animations:^{
    view.alpha = 1;
} completion:^(BOOL finished) {
    [UIView animateWithDuration:2 delay:1 options:0 animations:^{
        view.alpha = 0;
    } completion:nil];
}];
```

### Damping ratio and spring velocity

Damping ratio and spring velocity are new parameters introduced in iOS 7. Tune the parameters experimentally to achieve your desired result. Damping ratio is between 0 and 1, where low values oscillate more before settling to their final value. Spring velocity determines how quickly the animation begins as well as how much the animation will overshoot the final value before settling.

For example, the snippet below resizes the view with a very bouncy animation.

```
[UIView animateWithDuration:2 delay:0 usingSpringWithDamping:0.2 initialSpringVelocity:10 options:0 animations:^{
    CGRect endFrame = CGRectMake(view.frame.origin.x, view.frame.origin.y, view.frame.size.width * 2, view.frame.size.height * 2);
    view.frame = endFrame;
} completion:nil];
```
