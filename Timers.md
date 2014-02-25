Configure a simple repeating timer as in the snippet below. After calling the scheduledTimerWithTimeInterval method, the timer is immediately scheduled and will call the selector at the time interval.

```
NSTimer *timer = [NSTimer scheduledTimerWithTimeInterval:5 target:self selector:@selector(onTimer:) userInfo:nil repeats:YES];
```

### Canceling a timer

A timer retains the target, so be sure you cancel the timer at the appropriate time so that the target (which is often the view controller) can be released.

```
[timer invalidate];
```