View controllers are the backbone of an iOS application. For any given screen of an iPhone, there is generally one view controller. The view controller is responsible for creating the view that is displayed on the screen, as well as handling events and firing network requests associated with that screen.

## Creating Custom View Controllers

### Step 1: Creating a view controller

<img src="http://i.imgur.com/KiHA0yq.gif" width="726" height="489" />

To create a new view controller, click on File->New->File. You should name the view controller related to the content of the view controller. For example, a Twitter application might have a `TimelineViewController`, a `UserViewController`, and a `SettingsViewController`.

If you are **not** using Storyboard, make sure that "With XIB for user interface" is checked. If you are using Storyboard, make sure that it is unchecked. If you've accidentally checked it, you can always delete the .xib file afterwards.

### Step 2: Organizing within groups

In XCode, the folder structure within your project directory doesn't matter. Instead, you organize your files using "Groups" within XCode. Use the Command key (⌘) to select multiple files.

<img src="http://i.imgur.com/gZn1EXz.gif" height="302" width="292" />

## References

- [View Controller Programming Guide](https://developer.apple.com/library/ios/featuredarticles/ViewControllerPGforiPhoneOS/Introduction/Introduction.html)

