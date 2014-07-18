### Overview

This is a guide to displaying a preview of the camera and recording video using the PBJVision library.

### Step 1: Installation

#### 1. Create a Podfile in your project directory

```
platform :ios, '7.0'

pod 'PBJVision'
```

#### 2. Install the Pods

In the Terminal, type:

```
pod install
```

#### 3. Close your Xcode project and open the .xcworkspace file

### Step 2: Set up the video preview

#### 1. Create a placeholder view

The easiest way to control where the camera preview is going to appear is to create a view in Interface Builder that is placed and sized where you want the camera view to go.

Create an outlet for the preview view in the `@interface` area of your view controller.

```
@interface RecordViewController ()

@property (weak, nonatomic) IBOutlet UIView *previewView;

@end
```

#### 2. Add the Camera preview

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