<img src="http://i.imgur.com/omfSihU.gif" height="479" width="320" />

To create the tab bar controller in the image above, create a UITabBarController in the application delegate and set it to be the rootViewController of the window. Note that it is common for the UITabBarController's array of view controllers to be an array of navigation controllers. Sample code is [here].(https://github.com/thecodepath/ios_guides/tree/master/demos/tabbar)

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    
    UITabBarController *tabBarController = [[UITabBarController alloc] init];
    
    FirstViewController *firstViewController = [[FirstViewController alloc] init];
    UINavigationController *firstNavigationController = [[UINavigationController alloc] initWithRootViewController:firstViewController];
    
    SecondViewController *secondViewController = [[SecondViewController alloc] init];
    UINavigationController *secondNavigationController = [[UINavigationController alloc] initWithRootViewController:secondViewController];
    
    tabBarController.viewControllers = @[firstNavigationController, secondNavigationController];
    
    self.window.rootViewController = tabBarController;
    
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}
```

### Configuring the Tab Bar Item

You can configure the title, image, and selected image of the tab bar item in each view controller. Note that since the navigation controller is the actual view controller contained by the UITabBarController, you have to configure the tab bar item of the navigation controller, not the view controller.

```
- (void)viewDidLoad
{
    [super viewDidLoad];

    self.navigationController.tabBarItem.title = @"First";
    self.navigationController.tabBarItem.image = [UIImage imageNamed:@"House"];
}
```

