## Overview

Tab bars are one of the common types of navigation in iPhone apps, and they are easy to set up. Follow the steps below or check out the sample code [here](https://github.com/thecodepath/ios_guides/tree/master/demos/tabbar).

<img src="http://i.imgur.com/omfSihU.gif" height="479" width="320" />

### Step 1: Create the tab bar controller

To create the tab bar controller in the image above, create a UITabBarController in the application delegate and set it to be the rootViewController of the window. 

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    
    // Create the tab bar controller
    UITabBarController *tabBarController = [[UITabBarController alloc] init];
    
    self.window.rootViewController = tabBarController;
    
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}
```

### Step 2: Set the view controllers

Create a view controller for each tab that you want. It's common to have 2, 3, or 5 tabs in a tab bar.

#### Example 1: Creating two view controllers

```
// Create the two view controllers
FirstViewController *firstViewController = [[FirstViewController alloc] init];
SecondViewController *secondViewController = [[SecondViewController alloc] init];

tabBarController.viewControllers = @[firstViewController, firstViewController];
```

#### Example 2: Creating two view controllers within navigation controllers

Note that it is common for each view controller to be contained within a navigation controller. Each view controller has their own navigation controller because each tab has its own navigation history.

```
// Create the two view controllers, each within a navigation controller
FirstViewController *firstViewController = [[FirstViewController alloc] init];
UINavigationController *firstNavigationController = [[UINavigationController alloc] initWithRootViewController:firstViewController];
    
SecondViewController *secondViewController = [[SecondViewController alloc] init];
UINavigationController *secondNavigationController = [[UINavigationController alloc] initWithRootViewController:secondViewController];

tabBarController.viewControllers = @[firstNavigationController, secondNavigationController];
```

### Step 3: Configuring the Tab Bar Items

You can configure the title, image, and selected image of the tab bar item in each view controller. The snippet below demonstrates setting the title and icon of each of the tab bar items.

```
// Configure the titles and images of the tab bar items
firstNavigationController.tabBarItem.title = @"First";
firstNavigationController.tabBarItem.image = [UIImage imageNamed:@"House"];
    
secondNavigationController.tabBarItem.title = @"Second";
secondNavigationController.tabBarItem.image = [UIImage imageNamed:@"Martini"];
```

### Recap

Combine the 3 steps above to get a code snippet like the following:

```
#import "AppDelegate.h"
#import "FirstViewController.h"
#import "SecondViewController.h"

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    
    // Create the two view controllers, each within a navigation controller
    FirstViewController *firstViewController = [[FirstViewController alloc] init];
    UINavigationController *firstNavigationController = [[UINavigationController alloc] initWithRootViewController:firstViewController];
    firstNavigationController.tabBarItem.title = @"First";
    firstNavigationController.tabBarItem.image = [UIImage imageNamed:@"House"];

    SecondViewController *secondViewController = [[SecondViewController alloc] init];
    UINavigationController *secondNavigationController = [[UINavigationController alloc] initWithRootViewController:secondViewController];
    secondNavigationController.tabBarItem.title = @"Second";
    secondNavigationController.tabBarItem.image = [UIImage imageNamed:@"Martini"];

    // Configure the tab bar controller with the two navigation controllers
    UITabBarController *tabBarController = [[UITabBarController alloc] init];
    tabBarController.viewControllers = @[firstNavigationController, secondNavigationController];
        
    self.window.rootViewController = tabBarController;
    
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}
```
