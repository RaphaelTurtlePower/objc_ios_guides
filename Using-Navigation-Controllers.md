## Overview

Push/pop navigation is one of the common types of navigation in iPhone apps, and it is easy to set up. A navigation controller manages a stack of view controllers. It is always initialized with a view controller and view controllers can be pushed onto the stack or removed from the stack.

Follow the steps below to set up a navigation controller.

<img src="http://i.imgur.com/JBrxKdh.gif" height="568" width="320" />

### Step 1: Create the navigation controller

To create the navigation controller in the image above, create a UINavigationController in the application delegate and set it to be the rootViewController of the window. 

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    
    // Create the first view controller
    FirstViewController *vc = [[FirstViewController alloc] init];

    // Create the navigation controller
    UINavigationController *navigationController = [[UINavigationController alloc] initWithRootViewController:vc];
    
    self.window.rootViewController = navigationController;
    
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}
```

### Step 2: Push a view controller

In the event handler for a button or tapping a row in a table view, push a view controller.

```
- (IBAction)onTap:(id)sender {
    SecondViewController *vc = [[SecondViewController alloc] init];
    [self.navigationController pushViewController:vc animated:YES];
}
```

### Step 3: Popping a view controller

You get the back button automatically and tapping on the back button with remove the current view controller and go back to the previous view controller. If you want to remove the view controller manually, use the `popViewControllerAnimated:` method as below.

```
[self.navigationController popViewControllerAnimated:YES];
```
