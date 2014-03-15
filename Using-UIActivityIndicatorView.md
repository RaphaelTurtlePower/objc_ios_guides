## Overview

There is a built in loading indicator called UIActivityIndicatorView that you can use to display loading status. Follow the steps below to use the UIActivityIndicatorView

<img src="http://i.imgur.com/4HabDHa.gif" />

### Step 1: Create the UIActivityIndicatorView

You can either drag the UIActivityIndicator view into your nib file or create it programatically.

#### Example 1: Creating via Interface Builder

<img src="http://i.imgur.com/XA09IJX.gif" />

#### Example 2: Creating programatically

```
- (void)viewDidLoad {
   [super viewDidLoad];

   UIActivityIndicatorView *indicatorView = [[UIActivityIndicatorView alloc] initWithActivityIndicatorStyle:UIActivityIndicatorViewStyleWhite];
   indicatorView.center = self.view.center;
   [self.view addSubview:indicatorView];
}
```

### Step 2: Configuring properties

There are two interesting properties that you might want to configure with the UIActivityIndicatorView:

- color. Set the color of the indicator view, and it will override the color of the UIActivityIndicatorViewStyle.
- hidesWhenStopped. When the animation is stopped, the indicator will be automatically hidden. It will become visible again if it is restarted.

### Step 3: Starting and stopping the indicator view

This example assumes that the UIActivityIndicatorView is in the interface, either because it was linked via an IBOutlet or created programatically.

```
@interface

@property (nonatomic, strong) UIActivityIndicatorView *indicatorView;

@end
```

#### Start the spinning

```
[self.indicatorView startAnimating];
```

#### Stop the spinning

```
[self.indicatorView stopAnimating];
```
