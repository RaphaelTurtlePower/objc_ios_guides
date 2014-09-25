## Overview

This document is a guide to  the 1-day Objective-C for iOS workshop format to be run on a weekend for a group of  from **9am-5pm**. Organizers should be at the venue by **8am** to help setup.

## Student Prerequisites

The participants can be at any level of programming experience (we will sort you based upon skill level after arrival), but they may or may not be professional developers. We assume that most participants do not know Objective-C already.

Prior to the workshop, students will need a Mac computer running OSX 10.7 or later, with X-Code 4.5 or later. Please install X-Code from the Mac App Store. Keep in mind that you will need a strong internet connection to speed up this process. If you don’t know where to find this try your local Apple store.


<!-- ## Roles-->

<!--In order to run the workshop, we typically recommend 3-4 people helping out. There should be **1-2 instructors** and **1-2 TAs helping out**:-->

<!--* **Instructor** should be leading the session by giving step-by-step instructions and explaining each step and concept as it comes up. Might be completing the app on the projector alongside students. If there are multiple instructors, they might switch off to co-teach between sections of the day.
<!--* **TA** should be acting as support for the attendees circling around them during each step to ensure they don’t get stuck or left too far behind. The TAs should be the “eyes and ears” of the instructors to help adjust the pacing.-->

<!--## Tips-->

<!--* Most important thing is not to follow the schedule but that the group is able to follow along with the material on their computers. This is intended as a hands-on demo so we need to make sure that the majority of students are caught up.-->
<!--* During each scheduled break, TAs and instructors should circle around and check in with each student to get a sense of if they have had any problems keeping up with the previous section.-->
<!--* If certain people get too far behind the group, have them follow along by pairing them with another person sitting next to them who was able to follow along.-->


## Schedule

This is an approximate schedule. Remember to take the breaks because they are a good time to allow everyone to catch up.

* 9:30-10:00 am: **Breakfast and Arrival**
* 10:00-10:50 am: **Introduction**
* 10:50-11:00 am: **Break**
* 11:00-12:00 pm: **Tip Calculator**
* 12:00-1:00 pm: **Lunch**
* 1:00-1:30 pm:	**Objective-C Walkthrough**
* 1:30-2:50 pm:	**Rotten Tomatoes App**
* 2:50-3:00 pm:	**Break**
* 3:00-3:50 pm:	**Rotten Tomatoes Movie Detail View**
* 3:50-4:00 pm:	**Wrap Up**
* Bonus:	**Box Office and Top DVD Tabs**

### A. Introductions

**Duration:** 30 mins

* Instructor Introduction (5 minutes)
* CodePath Introduction (5 minutes)
    * "Professional organization for startup engineers. This includes mentorship and training, fellowship, and career development"
* Student Introductions (20 minutes)
    * Each person:  Say your name, describe your programming background, and why you want to learn iOS development?
    * Poll the class: How many of you already know an object-oriented programming language? Java/Ruby/Python/C#? How many do front-end web development? Back-end web development?
* Getting Started (5 minutes)
    * We are going to build a few simple applications together over the course of the workshop
    * Ask attendees how many of them have Xcode installed. Pair people that aren’t setup with a buddy
    * Ask if anyone has any questions so far before we continue.

### B. Tip Calculator

**Duration:** 50 mins
  
The purpose of the Tip Calculator app is to use a simple, but functional app to introduce Xcode. The takeaways of this session are:

* Creating a new project in Xcode
* Creating a view controller
* Designing a view in Interface Builder
* Using IBOutlets and IBActions to implement the dynamic behavior
  
When running this session, feel free to take your time introducing Xcode and Interface Builder. Consider glossing over the Objective-C questions and deferring to the Objective-C walkthrough in next session, so that you can stay high level.

1. Start by demonstrating the functioning [Tip Calculator](https://github.com/thecodepath/ios_tipster)
1. Create an empty Xcode project and run it in the simulator. Point out the various simulators.
1. Create a new view controller called TipViewController with a xib.
1. Set the TipViewController to be the rootViewController, change the background color of the view controller, and run it in the simulator.
1. Add the TipViewController to a navigation controller, set the title, and run again.
1. Layout the various views of the Tip Calculator and play with the available properties. (UILabel, UITextField, UISegmentedControl, UIView). Run again.
1. Create an IBOutlet for the totalLabel and demonstrate setting the text of the label in viewDidLoad.
1. Add a tap gesture recognizer to the view. In the action, NSLog that the user tapped in the view.
1. In the tap gesture handler, dismiss the keyboard using [self.view endEditing];
1. Wire up the remaining IBOutlets and implement the tip calculation.
1. Bonus: update the tip amount as the user is typing. Do not use UITextFieldDelegate. Instead, use the Editing Changed event by right clicking on the UITextField.

### C. Objective-C Walkthrough

**Duration:**  30 mins

The purpose of this section is to provide a broad overview of Objective-C and using the Xcode debugger. Tip: when typing out code in Objective-C, type the Java equivalent in a comment for each line.

* Declare variables of many different types, explain *
    * Basic types: int, float, BOOL
    * Common Foundation types: NSString, NSArray, NSDictionary, NSObject
    * Common structs: CGRect, CGSize, CGPoint
* Demonstrate logging
* Demonstrate setting breakpoints
* Create the void method sayHello
* Create the void method sayMyName with one parameter
* Create the void method sayMyName with two parameters (firstName, lastName)
* Create a Movie class, add properties for title, posterUrl, and synopsis
* Instantiate some Movie objects into an array, iterate through them, and print them out

### D. Rotten Tomatoes

**Duration:** 90 mins

1. Start by demonstrating the functioning [Rotten Tomatoes app](https://github.com/thecodepath/ios_tomatoes)
1. Create a new project and a view controller called MoviesViewController with a .xib.
1. Add a table view, create an outlet, and set the dataSource and delegate in viewDidLoad.
1. Implement the 2 required datasource methods: numberOfRows and cellForRowAtIndexPath. In numberOfRows, return 10. In cellForRowAtIndexPath, allocate a UITableViewCell (don’t use the dequeue method), and set the titleLabel of the cell to @”Hello”. Run in the simulator.
1. Create an array of names, and modify the dataSource methods to show the array of names.
1. Paste in [this snippet](https://gist.github.com/timothy1ee/8308396) to download the box office movies from the Rotten Tomatoes API.
    * Open the API url in Chrome to show the data. Tip: use a pretty json Chrome extension.
    * Modify the dataSource methods to print out the movie titles.
    * Discuss why you need to call reloadData.
1. Create a MovieCell with an UIImageView, and UILabels for the title and synopsis.
1. Register the MovieCell, dequeue it, and use it to print the title and synopsis.
1. Implement posters
    * Create a Podfile and add AFNetworking
    * #import “UIImageView+AFNetworking.h”

### E. RottenTomatoes Movie Detail View

**Duration:**  50 mins

1. Implement the didSelectRowAtIndexPath method, logging the touch.
1. Create the MovieDetailViewController that just has a UILabel for now. Add a public property for the movie dictionary.
1. In didSelectRowAtIndexPath, push a new MovieDetailViewController with the appropriate movie.
1. Style the MovieDetailViewController until it looks like the demo.
1. Bonus: Add a UIScrollView so that the synopsis can scroll.

### F. Bonus: Box Office and Top DVDs Tabs

**Duration:**  30 mins

1. In the App Delegate, create a UITabBarController and instantiate with two UINavigationControllers that each have a MoviesViewController as the rootViewController.
1. Add the tab bar images to Images.xcassets.
1. Add a type property to MoviesViewController to configure it for the Box Office or Top DVDs.

### G. Wrapping Up

**Duration:** 10 mins

* In a day, we’ve covered many of the basic topics required for building iOS apps including views, layouts, navigation, and networking. 
* Sign up with a [Parse account](https://parse.com/docs/android_guide)
    * Easy way to setup server-side database and API
* Think of a project you want to build and get started on it. Be sure to come to our meetup events.