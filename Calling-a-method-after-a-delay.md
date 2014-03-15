## Overview

It's often useful to call a method after a short delay, usually to time an animation. Follow the steps below to set this up.

### Step 1: Declare the method

In your interface, name the method that you want to be called after a delay.

```
@interface

- (void)myMethod;

@end
```

### Step 2: Implement the method

Implement the method with whatever code you want to run after a delay.

```
- (void)myMethod {
   // Whatever is in here will be run after the delay
}
```

### Step 3: Schedule the method

Use the `performSelector` method to schedule the method to be run after a delay.

```
// This will run "myMethod" after a 3 second delay.
[self performSelector:@selector(myMethod) withObject:nil afterDelay:3];
```
