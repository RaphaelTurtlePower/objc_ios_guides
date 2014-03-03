### Overview

UIKit Dynamics was introduced in iOS 7 to introduce a new level of realism to the UI. It's the same physics engine that powers SpriteKit except that it's set up to work with UIViews.

<img src="http://i.imgur.com/hmTooMm.gif" width="250" height="443" />

### Step 1: Create the UIDynamicAnimator

The UIDynamicAnimator is the brains behind the dynamics in the view. There is one instance of UIDynamicAnimator for all the dynamic views, it is the bridge between UIKit and the physics engine, and contains all the "behaviors" such as gravity and collision detection.

The UIDynamicAnimator is instantiated with a reference view, which is usually the root view of the UIViewController, i.e., `self.view`.

```
@interface MainViewController

@property (nonatomic, strong) UIDynamicAnimator *animator;

@end

@implementation MainViewController

- (void)viewDidLoad
{
    [super viewDidLoad];

    self.animator = [[UIDynamicAnimator alloc] initWithReferenceView:self.view];
}
```

### Step 2: Adding behaviors

You can create nearly any effect by using one or more of the available behaviors: gravity, push, snap, attachment, and collision. After creating the behavior, add it to the animator to enable it.

#### Example: Gravity

<img src="http://i.imgur.com/2RAjIi2.gif" width="250" height="443" />

```
NSArray *itemsWithGravity = @[self.greenView, self.blueView, self.redView];
UIGravityBehavior *gravityBehavior = [[UIGravityBehavior alloc] initWithItems:@[itemsWithGravity]];
[self.animator addBehavior:gravityBehavior];
```

At any time, you can add or remove views to the gravity behavior based on user input or some other condition.

```
[gravityBehavior addItem:self.greenView];
[gravityBehavior removeItem:self.blueView];
```
