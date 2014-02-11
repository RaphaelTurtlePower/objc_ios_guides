### XCode

#### Create an empty XCode project

There are a few new project templates in XCode, but it's best to start with the empty XCode project unless you want to use Storyboard. Click on File->New and create a new empty project.

<img src="http://i.imgur.com/tyZsMoL.png" width="731" height="494" />

#### Create a new view controller with a xib

After creating a new project, the first thing you'll want to do is to create a new view controller. Unless you're creating your view programatically, make sure you check the box for "With XIB for user interface".

<img src="http://i.imgur.com/aty5yvI.gif" width="727" height="488" />

#### Connecting an IBOutlet

If you want to access an object that you created in Interface Builder, you have to create an IBOutlet. For example, if you have a UILabel in the xib, and you want to set the text of the label in code, create an outlet for the UILabel. Click on the tuxedo in the upper right to open the Assistant Editor which puts the xib and code files next to each other. Make sure you control-click in order to draw the line for the outlet.

<img src="http://i.imgur.com/MKFzvh8.gif" width="678" height="340" />

### Objective-C

  - Importing the view controller into the app delegate (or any file that you want to use the view controller in)

```smalltalk
#import "MyViewController.h"

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
...
}

@end
```
  - Allocate a view controller

```smalltalk
MyViewController *myViewController = [[MyViewController alloc] init];
```

  - Setting the rootViewController of the window

```smalltalk
self.window.rootViewController = myViewController;
```

  - Create a CGRect frame

```smalltalk
CGRect frame = CGRectMake(0,0,100,20);
```

  - Allocate a view (UILabel, UIView, etc) w/ a frame

```smalltalk
UIView *view = [[UIView alloc] initWithFrame:frame];
UILabel *label = [[UILabel alloc] initWithFrame:labelFrame];
[view addSubview:label];
```

  - Set view properties

```smalltalk
view.backgroundColor = [UIColor blueColor];
```

  - Moving a UITextField when the keyboard appears and disappears

```smalltalk

@interface MainViewController ()

// Declare some methods that will be called when the keyboard is about to be shown or hidden
- (void)willShowKeyboard:(NSNotification *)notification;
- (void)willHideKeyboard:(NSNotification *)notification;

@end

- (id)initWithNibName:(NSString *)nibNameOrNil bundle:(NSBundle *)nibBundleOrNil
{
    self = [super initWithNibName:nibNameOrNil bundle:nibBundleOrNil];
    if (self) {
        // Register the methods for the keyboard hide/show events
        [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(willShowKeyboard:) name:UIKeyboardWillShowNotification object:nil];
        [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(willHideKeyboard:) name:UIKeyboardWillHideNotification object:nil];
    }
    return self;
}

- (void)willShowKeyboard:(NSNotification *)notification {
    NSDictionary *userInfo = [notification userInfo];
    
    // Get the keyboard height and width from the notification
    // Size varies depending on OS, language, orientation
    CGSize kbSize = [[userInfo objectForKey:UIKeyboardFrameBeginUserInfoKey] CGRectValue].size;
    NSLog(@"Height: %f Width: %f", kbSize.height, kbSize.width);

    // Get the animation duration and curve from the notification
    NSNumber *durationValue = userInfo[UIKeyboardAnimationDurationUserInfoKey];
    NSTimeInterval animationDuration = durationValue.doubleValue;
    NSNumber *curveValue = userInfo[UIKeyboardAnimationCurveUserInfoKey];
    UIViewAnimationCurve animationCurve = curveValue.intValue;
    
    // Move the view with the same duration and animation curve so that it will match with the keyboard animation
    [UIView animateWithDuration:animationDuration
                          delay:0.0
                        options:(animationCurve << 16)
                     animations:^{
                         self.commentImageView.frame = CGRectMake(0, self.view.frame.size.height - kbSize.height - self.commentImageView.frame.size.height, self.commentImageView.frame.size.width, self.commentImageView.frame.size.height);
                     }
                     completion:nil];
}

```