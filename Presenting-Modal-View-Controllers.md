### Overview

Any view controller may present another view controller with some animation, commonly sliding up from below or fading in. Of course, as in Inception, that view controller can present another view controller which can present another view controller and so on. However, the common use case is to present a compose view or settings view, as depicted below.

<img src="http://i.imgur.com/m0Mn9DU.gif" width="250" height="443" />&nbsp;&nbsp;<img src="http://i.imgur.com/4wESHoK.gif" width="250" height="443" />

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