### Overview

This is a guide to displaying a preview of the camera and recording video using the PBJVision library.

### Step 1: Installation

#### a. Create a Podfile in your project directory

```
platform :ios, '7.0'

pod 'PBJVision'
```

#### b. Install the Pods

In the Terminal, type:

```
pod install
```

#### c. Close your Xcode project and open the .xcworkspace file

### Step 2: Set up the video preview

#### a. Create a placeholder view

The easiest way to control where the camera preview is going to appear is to create a view in Interface Builder that is placed and sized where you want the camera view to go.

Create an outlet for the preview view in the `@interface` area of your view controller.

```
@interface RecordViewController ()

@property (weak, nonatomic) IBOutlet UIView *previewView;

@end
```

#### b. Add the Camera preview

Import the `PBJVision.h` header file at the top of the view controller .m file.

```
#import "PBJVision.h"
```

In the `viewDidLoad` method, add the camera preview into the placeholder previewView.

```
- (void)viewDidLoad
{
    [super viewDidLoad];

    AVCaptureVideoPreviewLayer *previewLayer = [[PBJVision sharedInstance] previewLayer];
    previewLayer.frame = self.previewView.bounds;
    previewLayer.videoGravity = AVLayerVideoGravityResizeAspectFill;
    [self.previewView.layer addSublayer:previewLayer];
    
    PBJVision *vision = [PBJVision sharedInstance];
    // vision.cameraDevice = PBJCameraDeviceBack;
    vision.cameraDevice = PBJCameraDeviceFront;
    vision.cameraMode = PBJCameraModeVideo;
    vision.cameraOrientation = PBJCameraOrientationPortrait;
    vision.focusMode = PBJFocusModeContinuousAutoFocus;
    vision.outputFormat = PBJOutputFormatSquare;
    vision.videoRenderingEnabled = YES;
    vision.additionalCompressionProperties = @{AVVideoProfileLevelKey : AVVideoProfileLevelH264Baseline30};
    
    [vision startPreview];
}
```

### Step 3: Recording Video

Use the following commands to control the video recording:

```
[[PBJVision sharedInstance] startVideoCapture];
[[PBJVision sharedInstance] pauseVideoCapture];
[[PBJVision sharedInstance] resumeVideoCapture];
[[PBJVision sharedInstance] endVideoCapture];
```

## Other Tasks

### Saving to Camera Roll

#### Step 1: Import Assets Framework

In the view controller that is recording your video, import the assets framework by including the following line at the top of your .m file.

```
#import <AssetsLibrary/AssetsLibrary.h>
```

#### Step 2: Save the video when recording stops

In order to save the video, we have to know when the recording stops. In the `viewDidLoad` method, set the view controller as the delegate of the `PBJVision` instance.

```
PBJVision *vision = [PBJVision sharedInstance];
vision.delegate = self;
```

Then, implement the following method:

```
- (void)vision:(PBJVision *)vision capturedVideo:(NSDictionary *)videoDict error:(NSError *)error
{
    // This is the path of the recorded video which is current in a temp directory on the phone
    NSString *videoPath = [videoDict objectForKey:PBJVisionVideoPathKey];

    // Move the video file from the temp directory to the camera roll
    ALAssetsLibrary *assetLibrary = [[ALAssetsLibrary alloc] init];
    [assetLibrary writeVideoAtPathToSavedPhotosAlbum:[NSURL URLWithString:videoPath] completionBlock:^(NSURL *assetURL, NSError *error1) {
        self.player.videoPath = assetURL.absoluteString;
        
        // Optionally, start playing the video.
        [self.player playFromBeginning];
    }];
}
```

For more details on how to play the recorded video, check out the [[Playing Embedded Video]] guide.