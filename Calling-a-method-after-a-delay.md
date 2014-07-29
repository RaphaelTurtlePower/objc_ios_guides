## Overview

It's often useful to call a method after a short delay, usually to time an animation. Follow the steps below to set this up.

### Step 1: Declare the method

In your interface, name the method that you want to be called after a delay.

```
@interface

// Can be a method with no parameter
- (void)myMethod;

// Can be a method with a single parameter
- (void)myMethodWithObject:(id)object;

@end
```

### Step 2: Implement the method

Implement the method with whatever code you want to run after a delay.

```
- (void)myMethod {
   // Whatever is in here will be run after the delay
}

- (void)myMethodWithObject:(id)object {
   // Whatever is in here will be run after the delay with the passed in object

   // For example, if the object is a UIView, you can cast it to a UIView.
   UIView *view = (UIView *)object;

   // Do something with the view
}
```

### Step 3: Schedule the method

Use the `performSelector` method to schedule the method to be run after a delay.

```
// This will run "myMethod" after a 3 second delay.
[self performSelector:@selector(myMethod) withObject:nil afterDelay:3];

// This will run "myMethodWithObject" after a 3 second delay with the passed in object. Note the ":" at the end of the method name.
[self performSelector:@selector(myMethod:) withObject:object afterDelay:3];
```
