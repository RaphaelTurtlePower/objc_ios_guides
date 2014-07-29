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

#### Adding/Removing Items from Gravity

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

### Collision

Since you may want to add or remove items from collision dynamically, you should create the collision behavior as a property.

```
@interface MainViewController

@property (nonatomic, strong) UICollisionBehavior *collision;

@end
```

In `viewDidLoad`, create the collision behavior and add it to the animator.

```
- (void)viewDidLoad {
    [super viewDidLoad];

    self.collision = [[UICollisionBehavior alloc] init]];
    [self.animator addBehavior:self.collision];
}
```

#### Adding/Removing Items from Collision

At any time, you can add or remove views to the collision behavior based on user input or some other condition.

```
[self.collision addItem:self.greenView];
[self.collision removeItem:self.blueView];
```

#### Setting up Boundaries

You can add arbitrary boundaries for objects to collide with. Choose an identifier, so that when a collision event happens, you can check which boundary an object collided with.

```
[self.collision addBoundaryWithIdentifier:@"shelf" fromPoint:CGPointMake(0, 200) toPoint:CGPointMake(150, 240)];
```

You can set the bounds of the view to automatically be boundaries by setting the `translatesReferenceBoundsIntoBoundaries` property.

```
self.collision.translatesReferenceBoundsIntoBoundary = YES;
```

#### Detecting collisions

In order to detect collisions, you have to first set the collisionDelegate.

```
self.collision.collisionDelegate = self;
```

Then, in the .h file of your view controller, declare that you implement the UICollisionDelegate protocol.

```
@interface MainViewController : UIViewController <UICollisionBehaviorDelegate>

...

@end
```

Implement one of the appropriate collision events, e.g., collision between two objects or collision between an object and a boundary.

For example, to detect the collision of an object with a boundary, implement the following method:

```
- (void)collisionBehavior:(UICollisionBehavior*)behavior beganContactForItem:(id <UIDynamicItem>)item withBoundaryIdentifier:(id <NSCopying>)identifier atPoint:(CGPoint)p {
    // You have to convert the identifier to a string
    NSString *boundary = (NSString *)identifier;

    // The view that collided with the boundary has to be converted to a view
    UIView *view = (UIView *)item;

    if ([boundary isEqualToString:@"shelf"]) {
        // Detected collision with a boundary called "shelf"
    } else if (boundary == nil) {
        // Detected collision with bounds of reference view
    }
}
```

To detect the collision of an object with another object, implement the following method:

```
- (void)collisionBehavior:(UICollisionBehavior*)behavior beganContactForItem:(id <UIDynamicItem>)item1 withItem:(id <UIDynamicItem>)item2 atPoint:(CGPoint)p {
    UIView *view1 = (UIView *)item1;
    UIView *view2 = (UIView *)item2;
}
```

### Push

Since you may want to add or remove items from push dynamically, you should create the push behavior as a property.

```
@interface MainViewController

@property (nonatomic, strong) UIPushBehavior *push;

@end
```

In `viewDidLoad`, create the push behavior and add it to the animator.

```
- (void)viewDidLoad {
    [super viewDidLoad];

    self.push = [[UIPushBehavior alloc] init]];
    [self.animator addBehavior:self.push];
}
```

#### Adding/Removing Items from Push

At any time, you can add or remove views to the push behavior based on user input or some other condition.

```
[self.push addItem:self.greenView];
[self.push removeItem:self.blueView];
```

#### Direction of Push

You can change the direction and force of the push force by modifying the `pushDirection` property.

```
// Push goes down, but 1/10 the force of gravity
self.push.pushDirection = CGVectorMake(0,0.1);

// Push goes up
self.push.pushDirection = CGVectorMake(0,-1);

// Push goes diagonal
self.push.pushDirection = CGVectorMake(1,1);
```