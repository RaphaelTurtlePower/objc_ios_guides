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