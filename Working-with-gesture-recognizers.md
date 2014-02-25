### Setting up a Gesture recognizer

There are a variety of gesture recognizers available with the framework, and you can build your own gesture recognizers. Choose from the following builtin gesture recognizers:

- UITapGestureRecognizer
- UILongPressGestureRecognizer
- UIPanGestureRecognizer
- UIPinchGestureRecognizer
- UIRotationGestureRecognizer
- UIScreenEdgePanGestureRecognizer

Create and add a gesture recognizer to a view as in the snippet below.

```
UITapGestureRecognizer *tapGestureRecognizer = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(onTap:)];
[self.view addGestureRecognizer:tapGestureRecognizer];
```

### Gesture recognizer states

Gesture recognizers call the same selector as it transitions through states. For example, a pan gesture recognizer calls the selector that the user touches down on the view, and then it calls the selector repeatedly as the user drags their finger across the screen, and finally it calls the selector one last time when the user lifts their finger off the screen.

```
- (void)onPan:(UIPanGestureRecognizer *)panGestureRecognizer {
    CGPoint point = [panGestureRecognizer locationInView:self.view];
    CGPoint velocity = [panGestureRecognizer velocityInView:self.view];
    
    if (panGestureRecognizer.state == UIGestureRecognizerStateBegan) {
        NSLog(@"Gesture began at: %@", NSStringFromCGPoint(point));
    } else if (panGestureRecognizer.state == UIGestureRecognizerStateChanged) {
        NSLog(@"Gesture changed: %@", NSStringFromCGPoint(point));
    } else if (panGestureRecognizer.state == UIGestureRecognizerStateEnded) {
        NSLog(@"Gesture ended: %@", NSStringFromCGPoint(point));
    }
}
```
