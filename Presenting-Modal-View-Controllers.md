## Overview

Any view controller may present another view controller with some animation, commonly sliding up from below or fading in. Of course, as in Inception, that view controller can present another view controller which can present another view controller and so on. However, the common use case is to present a single view controller that will be dismissed shortly, as depicted below.

<img src="http://i.imgur.com/m0Mn9DU.gif" width="250" height="443" />&nbsp;&nbsp;<img src="http://i.imgur.com/4wESHoK.gif" width="250" height="443" />&nbsp;&nbsp;<img src="http://i.imgur.com/KpX7FcB.gif" width="250" height="443" />

This is a quick guide to presenting and dismissing view controllers.

### Step 1: Importing the view controller

In the implementation file of your view controller, import the view controller that you want to present.

```
#import "MainViewController.h"

// Import the view controller that you want to present
#import "ModalViewController.h"

@implementation MainViewController
...
@end
```

### Step 2: Presenting the view controller

The modal view controller is usually presented in a button handler method. Choose the transition style (rise from below, flip, curl, and fade) and call the present method. Note that you set the transition style on the view controller to be presented, not the current view controller.

#### Example #1 - Presenting a basic view controller

```
- (IBAction)onButton:(id)sender {
   UIViewController *vc = [[ModalViewController alloc] init];
   vc.modalTransitionStyle = UIModalTransitionStyleCoverVertical; // Rises from below

   // vc.modalTransitionStyle = UIModalTransitionStyleCrossDissolve; // Fade
   // vc.modalTransitionStyle = UIModalTransitionStyleFlipHorizontal; // Flip
   // vc.modalTransitionStyle = UIModalTransitionStylePartialCurl; // Curl

   [self presentViewController:vc animated:YES completion:nil];
}
```

#### Example #2 - Presenting a view controller with a navigation bar

Often, the view controller will be embedded in a navigation controller whether or not it actually needs the navigation stack. It is common to have a navigation bar on all views, and modal view controllers often have a "Done" or "Cancel" button in the navigation bar. You can set the modalTransitionStyle on either the navigation controller or the modal view controller.

```
- (void)onButton:(id)sender {
   UIViewController *vc = [[ModalViewController alloc] init];
   UINavigationController *navigationController = [[UINavigationController alloc] initWithRootViewController:vc];
   navigationController.modalTransitionStyle = UIModalTransitionStyleCoverVertical; // Rises from below

   [self presentViewController:navigationController animated:YES completion:nil];
}
```

### Step 3: Dismissing the view controller

A common UI for modal view controllers is to have a "Done" or "Cancel" button in the navigation bar, although your UI may have a different way of dismissing the view controller. Putting a "Done" button in the navigation bar looks something like this:

```
- (void)viewDidLoad
{
   [super viewDidLoad];

   UIBarButtonItem *doneButton = [[UIBarButtonItem alloc] initWithTitle:@"Done" style:UIBarButtonItemStyleDone target:self action:@selector(onDoneButton:)];
   self.navigationItem.rightBarButtonItem = doneButton;
}
```

To dismiss the view controller, simply call the dismiss method. Even though the view controller is embedded in a navigation controller, you can call the dismiss method directly on the modal view controller.

```
- (void)onDoneButton:(id)sender {
    [self dismissViewControllerAnimated:YES completion:nil];
}
```

## References

- [View Controller Programming Guide - Presenting View Controllers](https://developer.apple.com/library/ios/featuredarticles/ViewControllerPGforiPhoneOS/ModalViewControllers/ModalViewControllers.html)