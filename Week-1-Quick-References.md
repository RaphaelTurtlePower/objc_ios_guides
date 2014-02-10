### XCode

#### Create an empty XCode project

There are a few new project templates in XCode, but it's best to start with the empty XCode project unless you want to use Storyboard. Click on File->New and create a new empty project.

<img src="http://i.imgur.com/tyZsMoL.png" width="731" height="494" />

#### Create a new view controller with a xib

After creating a new project, the first thing you'll want to do is to create a new view controller. Unless you're creating your view programatically, make sure you check the box for "With XIB for user interface".

<img src="http://i.imgur.com/aty5yvI.gif" width="727" height="488" />

#### Connecting an IBOutlet

If you want to access an object that you created in Interface Builder, you have to create an IBOutlet. For example, if you have a UILabel in the xib, and you want to set the text of the label in code, create an outlet for the UILabel. Click on the tuxedo in the upper right to open the Assistant Editor which puts the xib and code files next to each other. Make sure you control-click in order to draw the line for the outlet.

<img src="http://i.imgur.com/MKFzvh8.gif" width="678" height="340" />

### Objective-C
  - Importing the view controller into the app delegate
  - Allocate a view controller
  - Create a CGRect frame
  - Allocate a view (UILabel, UIView, etc) w/ a frame
  - Set view properties
  - Setting the rootViewController of the window

