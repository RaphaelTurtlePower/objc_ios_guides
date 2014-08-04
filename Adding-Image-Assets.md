Asset Catalogs are a new feature in XCode 5, and it makes asset management easy. To add assets to a project, follow the steps below.

<img src="http://i.imgur.com/gPEbazB.gif" />

### Step 1: Select the asset catalog

As in the screenshot above, click Images.xcassets in the project navigator to bring up the Asset Catalog for the project.

### Step 2: Add Image Set

To add an image to the project, create a new image set. Drag the png asset (jpeg won't work) to the 1X or 2X slot. In a production app, you should include both the standard (1X) as well as retina (2X) asset. During development, you can add only one asset and XCode will automatically create the other one, although it may look blurry.

### Step 3: Using the image set

#### Example 1: Using the image set in Interface Builder

Any control that has images like UIImageViews or UIButtons can set images in Interface Builder. Any image set in the Asset Catalog will be listed in the image drop down menus.

<img src="http://i.imgur.com/hPVX8b3.gif" width="301" height="226" />

#### Example 1: Using the image set programatically

To access images in the Asset Catalog programatically, create UIImages using the `imageNamed:` method as shown in the snippet below.

**Objective-C**
```
UIImage *chat = [UIImage imageNamed:@"Chat"];
UIImageView *chatImageView = [[UIImageView alloc] initWithImage:chat];
```