## Overview

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

It is common to create the gesture recognizers in the `viewDidLoad` method, as shown below. After you create the gesture recognizer, attach it to the view you want to detect gestures on.

#### Example 1: Tap gesture recognizer

```
- (void)viewDidLoad {
   // The onCustomTap: method will be defined in Step 3 below.
   UITapGestureRecognizer *tapGestureRecognizer = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(onCustomTap:)];

   // Optionally set the number of required taps, e.g., 2 for a double click
   tapGestureRecognizer.numberOfTapsRequired = 2;

   // Attach it to a view of your choice. If it's a UIImageView, remember to enable user interaction
   [self.view addGestureRecognizer:tapGestureRecognizer];
}
```

#### Example 2: Pan gesture recognizer

```
- (void)viewDidLoad {
   // The onCustomPan: method will be defined in Step 3 below.
   UIPanGestureRecognizer *panGestureRecognizer = [[UIPanGestureRecognizer alloc] initWithTarget:self action:@selector(onCustomPan:)];

   // Attach it to a view of your choice. If it's a UIImageView, remember to enable user interaction
   [self.view addGestureRecognizer:panGestureRecognizer];
}
```

### Step 3: Implement the event handler method

When the gesture recognizer detects the gesture, it will call the event handler method on the target. The event handler method is specified when you created the gesture recognizer in Step 2. Declare the method in the interface and implement it.

Gesture recognizers call the same selector as it transitions through various states. For example, a pan gesture recognizer calls the selector when the user first touches down on the view, and then it calls the selector repeatedly as the user drags their finger across the screen, and finally it calls the selector one last time when the user lifts their finger off the screen.

#### Example 1: Tap gesture recognizer

```
@interface YourViewController

// If you're using a different gesture recognizer (pinch, pan, etc), be sure to change the type below.
- (void)onCustomTap:(UITapGestureRecognizer *)tapGestureRecognizer;

@end
```

```
@implementation YourViewController

- (void)onCustomTap:(UITapGestureRecognizer *)tapGestureRecognizer {
   CGPoint point = [tapGestureRecognizer locationInView:self.view];

   // User tapped at the point above. Do something with that if you want.
}

```

#### Example 2: Pan gesture recognizer

```
@interface YourViewController

// If you're using a different gesture recognizer (pinch, pan, etc), be sure to change the type below.
- (void)onCustomPan:(UIPanGestureRecognizer *)panGestureRecognizer;

@end
```

```
@implementation YourViewController

- (void)onCustomPan:(UIPanGestureRecognizer *)panGestureRecognizer {
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

## Other Gesture Recognizer Tasks

Below are some common tasks that you might have with gesture recognizers.

### Using Simultaneous Gesture Recognizers

By default, it won't work if you add multiple gesture recognizers to the same view. In order to do that, you have to specifically enable it.

#### Step 1: Set the Gesture Recognizer delegate

For example, if you want to use a pinch and rotate gesture recognizer simultaneously, choose either the pinch or the rotate gesture recognizer (it doesn't matter which one). If you created the gesture recognizer in Interface Builder, create an IBOutlet for it by Ctrl-dragging from the nib.

```
self.pinchGestureRecognizer.delegate = self;
```

#### Step 2: Implement the Gesture Recognizer protocol

Go to the header file of the view controller and add UIGestureRecognizerDelegate to the list of protocols, as shown below.

```
@interface MainViewController : UIViewController <UIGestureRecognizerDelegate>
...
@end
```

Copy the following UIGestureRecognizerDelegate method into the implementation (.m) file.

```
- (BOOL)gestureRecognizer:(UIGestureRecognizer *)gestureRecognizer shouldRecognizeSimultaneouslyWithGestureRecognizer:(UIGestureRecognizer *)otherGestureRecognizer {
    return YES;
}
```

Now the pinch and scale gesture recognizers should work simultaneously.

