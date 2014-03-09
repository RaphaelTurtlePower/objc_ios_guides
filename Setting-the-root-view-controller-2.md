When the application first launches, you'll want to configure an initial view controller to launch first. For example, most apps will launch a view controller that will allow a user to login to the application.

Follow the steps below to configure the initial view controller of an application

### Step 1: Import the view controller

In `AppDelegate.m`, import the view controller that you want to launch.

```
#import "AppDelegate.h"
#import "MainViewController.h"   // Import whatever view controller you want to use

@implementation AppDelegate
...
@end
```

### Step 2: Set the root view controller

In `AppDelegate.m`, there is a method called `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions` that is called immediately after the application launches.

In the method, create an instance of your view controller and set the `rootViewController` property of the `window`.

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    
    MainViewController *vc = [[MainViewController alloc] init];
    self.window.rootViewController = vc;
    
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}
```
