This is a guide for embedding and playing videos in any view. You can start, pause, and stop the video and configure it to loop. You can resize the video and add it as a subview to any view.

### Step 1: Installation

#### a. Create a Podfile in your project directory

```
platform :ios, '7.0'

pod 'PBJVideoPlayer'
pod 'HCYoutubeParser'
```

#### b. Install the Pods

In the Terminal, type:

```
pod install
```

#### c. Close your Xcode project and open the .xcworkspace file

### Step 2: Set up the Player

#### a. Add a property for the player

In the `@interface` area of your view controller, declare the property.

```
@interface SplashViewController ()

@property (nonatomic, strong) PBJVideoPlayerController *player;

@end
```

#### b. Add the Player to the view

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

#### c. Play the video

You can immediately start playing the video in the `viewDidLoad` method or you can trigger it on button press.

For example, get the url for a YouTube video like this:

```
NSURL *url = [NSURL URLWithString:@"https://www.youtube.com/watch?v=GuX52wkCIJA"];
NSDictionary *videos = [HCYoutubeParser h264videosWithYoutubeURL:url];

NSString *hdUrl = videos[@"hd720"];
NSString *mediumUrl = videos[@"medium"];
```

To play the medium resolution YouTube video above, do the following:

```
self.player.videoPath = mediumUrl;
[self.player playFromBeginning];
```
