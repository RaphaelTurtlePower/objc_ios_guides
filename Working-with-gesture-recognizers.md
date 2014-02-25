### Overview

Gesture recognizers are a powerful and easy to use tool for handling user gestures like tap or pinch and performing actions like triggering animations or view changes. This is a quick guide for the steps in setting up gesture recognizers.

### Step 1: Choose a gesture recognizer

There are many builtin gesture recognizers in iOS, and you can also create your own. Choose one from the following list.

- UITapGestureRecognizer. Can be configured with the number of required taps to handle single, double, or more taps.
- UILongPressGestureRecognizer. Can be configured with the required delay to be considered a long press. Defaults to 0.5 s.
- UIPanGestureRecognizer
- UIPinchGestureRecognizer. Used for pinch in and pinch out, this gesture recognizer continuously outputs to a `scale` property as the user moves their finger.
- UIRotationGestureRecognizer. Continuously outputs to `rotation` in radians.
- UIScreenEdgePanGestureRecognizer. Can be configured with which edge to detect pans from. Only detects pan movements that begin from the specified edge.

### Step 2: Instantiate the gesture recognizer

It is common to create the gesture recognizers in the `viewDidLoad' method, as shown below. After you create the gesture recognizer, attach it to the view you want to detect gestures on.

```
- (void)viewDidLoad {
   // The onTap: method will be defined in Step 3 below.
   UITapGestureRecognizer *tapGestureRecognizer = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(onTap:)];

   // Attach it to a view of your choice. If its a UIImageView, remember to enable user interaction
   [self.view addGestureRecognizer:tapGestureRecognizer];
}
```

### Step 3: Implement the event handler method

When the gesture recognizer detects the gesture, it will call the event handler method on the target. The event handler method is specified when you created the gesture recognizer in Step 2. Declare the method in the interface and implement it.

```
@interface YourViewController

// If you're using a different gesture recognizer (pinch, pan, etc), be sure to change the type below.
- (void)onTap:(UITapGestureRecognizer *)tapGestureRecognizer;

@end
```

```
@implementation YourViewController

- (void)onTap:(UITapGestureRecognizer *)tapGestureRecognizer {
   // Implement your magic here.
}

```

### Step 4: Handling events

Gesture recognizers call the same selector as it transitions through states. For example, a pan gesture recognizer calls the selector when the user first touches down on the view, and then it calls the selector repeatedly as the user drags their finger across the screen, and finally it calls the selector one last time when the user lifts their finger off the screen.

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
