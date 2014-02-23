Downloading an image into a UIImageView is a common task. UIImageView doesn't support setting an image URL; it expects you to download the image in a background thread, optionally cache it, and set the image property of the UIImageView.

To make this process easier, there are many libraries that have added a category method to UIImageView to automatically download, cache, and set the image.

### Add AFNetworking to the project

Add AFNetworking to the project by downloading it [here](https://github.com/AFNetworking/AFNetworking) (click on Download ZIP on the right toolbar). Open the AFNetworking folder and drag the subfolders called AFNetworking and UIKit+AFNetworking into your project. Be sure to click "Copy items into destination folder".

<img src="http://i.imgur.com/kTyujQ0.gif" width="693" height="287"/>

### Using UIImageView+AFNetworking

In the file that has your UIImageView, import the UIImageView+AFNetworking category.

```
#import "UIImageView+AFNetworking.h"
```

Then, simply use the method that AFNetworking adds to UIImageView.

```
NSURL *url = [NSURL URLWithString:@"http://
[imageView setImageWithURL:url];

// Or, optionally set a placeholder image to use while the image is downloading

[imageView setImageWithURL:url placeholderImage:placeholder];
```


