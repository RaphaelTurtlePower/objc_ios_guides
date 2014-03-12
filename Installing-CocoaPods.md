## Overview

There is no official Apple mechanism for handling dependency management for iOS projects. An open source project called CocoaPods was created to 

### Step 1: Install RubyGems

Follow the instructions [here](http://rubygems.org/pages/download).

If you already have RubyGems, make sure it's updated to the latest version. To update it, run the following command:

```
gem update --system
```

### Step 2: Install CocoaPods

Run the two commands below to install CocoaPods.

```
sudo gem install cocoapods
pod setup
```

### Step 3: Setting up a CocoaPods project

You can use CocoaPods with a new project or an existing project by following the steps below:

Open Terminal and navigate to the directory with the XCode project file.
Create a new Podfile for the project.  For example, the Podfile below is for a project who's deployment version is 6.1 and includes two libraries.

```
platform :ios, '7.0'

pod 'AFNetworking'
```

### Step 4: Installing dependencies

Run the command `pod install` in Terminal. You'll need to run this every time you modify the Podfile. If you've removed dependencies from the Podfile, running this command will remove that dependency from your Pods project.

Don't open the XCode project file anymore!  From now on, just open the XCode workspace file, which will include your original project file and now also have the Pods project file with all the dependencies.