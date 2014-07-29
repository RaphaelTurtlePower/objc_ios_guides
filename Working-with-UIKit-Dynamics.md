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

### Gravity

<img src="http://i.imgur.com/2RAjIi2.gif" width="250" height="443" />

Since you may want to add or remove items from gravity dynamically, you should create the gravity behavior as a property.

```
@interface MainViewController

@property (nonatomic, strong) UIGravityBehavior *gravity;

@end
```

In `viewDidLoad`, create the gravity behavior and add it to the animator.

```
- (void)viewDidLoad {
    [super viewDidLoad];

    self.gravity = [[UIGravityBehavior alloc] init]];
    [self.animator addBehavior:self.gravity];
}
```

#### Adding/Removing items from gravity

At any time, you can add or remove views to the gravity behavior based on user input or some other condition.

```
[self.gravity addItem:self.greenView];
[self.gravity removeItem:self.blueView];
```

#### Direction of Gravity

You can change the direction and force of gravity by modifying the `gravityDirection` property.

```
// Gravity still goes down, but at a reduced force
self.gravity.gravityDirection = CGVectorMake(0,0.1);

// Gravity goes up
self.gravity.gravityDirection = CGVectorMake(0,-1);

// Gravity goes diagonal
self.gravity.gravityDirection = CGVectorMake(1,1);
```
