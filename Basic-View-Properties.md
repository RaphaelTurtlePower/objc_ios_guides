## Overview

The commonly used view properties are:

- backgroundColor
- alpha
- frame
- center
- transform

There are a few additional properties for the view that are set on the underlying CALayer. A View is just a wrapper around a CALayer.

- cornerRadius
- border
- shadow

<img src="http://i.imgur.com/j5SStM8.png" width="324" height="484" />

### Setting view properties

See the code snippet below for an example of setting view properties, including the properties available on the layer.

```
- (void)viewDidLoad
{
    [super viewDidLoad];
    
    self.blueView.backgroundColor = [UIColor blueColor];
    self.blueView.alpha = 0.8;
    
    self.blueView.layer.borderColor = [UIColor grayColor].CGColor;
    self.blueView.layer.borderWidth = 10;
    
    self.blueView.layer.cornerRadius = 10;
    
    self.blueView.layer.shadowColor = [UIColor blackColor].CGColor;
    self.blueView.layer.shadowOffset = CGSizeMake(5, 5);
    self.blueView.layer.shadowOpacity = 0.8;
    self.blueView.layer.shadowRadius = 3;
}
```
