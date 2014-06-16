## This class is not key value coding-compliant for the key 'xxx'

![Key value error screenshot](http://i.imgur.com/wfWpNOX.png)

The top part of the screenshot isn't helpful as many runtime exceptions look like that. The key is to read the error message in the console area at the bottom of the screen.

```
Terminating app due to uncaught exception 'NSUnknownKeyException', reason: '[<MainViewController 0x8c56940> setValue:forUndefinedKey:]: this class is not key value coding-compliant for the key textLabel.'
```

This happens after you create an IBOutlet or IBAction by Ctrl-dragging from Interface Builder to the implementation file. After creating the outlet or action and you subsequently change the property name or delete it, you will get this runtime error.

The problem is that the .xib file was still expecting the original name which was later changed.

### Solution

Open the .xib file of the view controller that's named in the error message. In the example above, it was in `MainViewController`.

1. Click on the File's Owner (looks like a yellow, hollow cube) and click on the Connections Inspector (top right of Xcode, it's a white arrow in a blue circle).
2. Click the 'x' next to the Outlet or Action that you changed to delete the connection.

![Fix Broken Connection](http://i.imgur.com/hsOeiuu.png)