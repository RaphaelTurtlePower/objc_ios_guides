### Step 1: Installation

#### 1. Create a Podfile in your project directory

```
platform :ios, '7.0'

pod 'PBJVideoPlayer'
pod 'HCYoutubeParser'
```

#### 2. Install the Pods

In the Terminal, type:

```
pod install
```

#### 3. Close your Xcode project and open the .xcworkspace file

### Step 2: Set up the Player

#### 1. Add a property for the player

In the `@interface` area of your view controller, declare the property.

```
@interface SplashViewController ()

@property (nonatomic, strong) PBJVideoPlayerController *player;

@end
```

#### 2. Add the Player to the view

In the `viewDidLoad` method, create the player and add the view to your main view whereever you want.

```
- (void)viewDidLoad
{
    [super viewDidLoad];

    // Create the player and choose the size and position
    self.player = [[PBJVideoPlayerController alloc] init];
    self.player.view.frame = CGRectMake(0, 180, 320, 180);
    
    // Add the player's view to your subview
    [self addChildViewController:self.player];
    [self.view addSubview:self.player.view];
    [self.player didMoveToParentViewController:self];
}
```

#### 3. Play the video

You can immediately start playing the video in the `viewDidLoad` method or you can trigger it on button press.

For example, get the url for a YouTube video like this:

```
NSURL *url = [NSURL URLWithString:@"https://www.youtube.com/watch?v=GuX52wkCIJA"];
NSDictionary *videos = [HCYoutubeParser h264videosWithYoutubeURL:url];

NSString *hdUrl = videos[@"hd720"];
NSString *mediumUrl = videos[@"hd720"];
```

To play the medium resolution YouTube video above, do the following:

```
self.player.videoPath = mediumUrl;
[self.player playFromBeginning];
```
