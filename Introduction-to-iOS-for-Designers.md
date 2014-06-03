This bootcamp is optimized for empowering designers to modify the view and animation related code for production apps. As such, there is a focus on views, navigation, transitions, and animations. Topics such as networking, threading, models, and device frameworks for accessing the camera and location are not covered. In addition, there is a focus on techniques currently used in production such as programmatic views and springs and struts over Interface builder and Auto Layout.

In terms of prototyping, the goal of the class is to provide the tools necessary to build rich, interactive mocks using Objective-C instead of Quartz Composer and other tools. While the bootcamps will not cover enough topics to make the prototypes fully functional, that would be the logical next step.

## Course Policies

In order to finish the course successfully, there are a few course policies:

- Attendance. There is one excused absence allowed where acceptable excuses include illness, work, or personal travel. If you have travel plans, please let me know as soon as possible. No unexcused absences are allowed.
- Weekly homework submissions. There is weekly homework described in the course schedule below. Submission instructions are in the detailed links.

## Course Schedule

In the course schedule below, each week has two 2-hour sessions where we will cover about a dozen different use cases related to the topic of the week. Each week has a "skills checklist" that you should be able to do by the end of the week. Each week also has a homework that applies the use cases that we cover in class.

### Week 1 - Basic views and layout

We will be covering laying out basic views such as labels, images, and buttons in Interface Builder and programatically. We will be covering topics and use cases such as the following:

- Basic
  - Creating an empty XCode project and running in the simulator
  - Adding standard and retina image assets to a project
  - Changing the app icon and splash screen
- Views and properties
  - Views, Labels, Images, Buttons, Text Fields
  - Interface Builder vs. Programmatic view design
- Basic usage of navigation and tab bars

#### Homework

The homework this week is to make a non-scrollable version of a detailed view of a Facebook post. Full homework description is [[here|Week 1 Homework]].

<img src="http://i.imgur.com/N8PfLlf.png" width="250"/>&nbsp;&nbsp;<img src="http://i.imgur.com/bzanQSb.png"  width="250" />

#### Other links

- [[Week 1 Skills checklist|Designer Week 1 Skills Checklist]]
- Week 1 Quick References
  - XCode
     - [[Creating an XCode project]]
     - [[Connecting IBOutlets]]
     - [[Adding Image Assets]]
  - View Controllers
     - [[Introduction to View Controllers]]
     - [[Setting the Root View Controller]]
  - Navigation
     - [[Using Navigation Controllers]]
     - [[Using Tab Bar Controllers]]
  - Views
     - [[Basic view properties]]
  - Keyboard
     - [[Getting the keyboard height]]

### Week 2 - Events and States

We will be covering events and delegates and making stateful applications. We will be covering topics and use cases such as the following:

- Events and Delegates
  - Events via targets and selectors
  - Delegation for simple controls like UIAlertView and UIActionSheet
  - Handling UITextField delegate events
  - Handling scroll view events
  - Observing properties using KVO
- Application states
  - Mocking an transient loading state
  - Transitioning between empty and populated states
  - Performing selectors after delays

#### Homework

The homework this week is to implement the Facebook login flow with loading and error states. Full homework description is [[here|Week 2 Homework]].

<img src="http://i.imgur.com/HscRliMl.png" width="250" />&nbsp;&nbsp;<img src="http://i.imgur.com/tQA52bkl.png" width="250"/>

#### Other links

- [[Week 2 Skills checklist|Designer Week 2 Skills Checklist]]
- Week 2 Quick References
  - [[Using UIActivityIndicatorView]]
  - [[Using UIAlertView and UIActionSheet]]
  - [[Presenting Modal View Controllers]]
  - [[Calling a method after a delay]]
  - [[Using UIScrollView]]
  - [[Working with the keyboard]]

### Week 4 - Animation and Gestures

We will be covering view animations and interactions via gestures such as tap, pan, swipe, pinch, and rotate. We will be covering topics and use cases such as the following:

- Animation
  - Animation of properties such as color, frame, and alpha
  - Animation options such as repeat and reverse
  - Damping ratio and spring velocity
  - Working with affine transforms
- Gestures
  - Attaching gestures to views
  - Accessing location, velocity, rotation, and scale
  - Processing gesture state

#### Homework

The homework this week is to make an interactive mock of the Paper navigation. Full homework description is [[here|Week 4 Homework]].

<img src="http://i.imgur.com/1BNYyRK.gif" width="250"/>&nbsp;&nbsp;<img src="http://i.imgur.com/LUlV6x1.gif" width="250"/>

#### Other links

- [[Week 4 Skills checklist|Designer Week 4 Skills Checklist]]
- Week 4 Quick References
  - [[Basic animation]]
  - [[Working with gesture recognizers]]
  - [[Timers]]

### Week 3 - Custom feeds

We will be covering creating custom UITableViews with dynamic row heights populated with modeled data. We will be covering topics and use cases such as the following:

- Table Views
  - Specifying the number of rows and sections
  - Designing custom cells
  - Using plain and grouped table views
  - Setting headers and footers
- Models
  - Specifying model properties
  - Instantiating fake data

#### Homework

The homework this week is to make a scrollable version of the Facebook notifications view. Full homework description is [[here|Week 3 Homework]].

<img src="http://i.imgur.com/7IuFoEul.png" width="250"/>&nbsp;&nbsp;<img src="http://i.imgur.com/N8PfLlf.png" width="250"/>

#### Other links

- [[Week 3 Skills checklist|Designer Week 3 Skills Checklist]]
- Week 3 Quick References
  - [[Creating a Model]]
  - [[Working with UITableView]]
  - [[Using Tab Bar Controllers]]
  - [[Downloading an image into UIImageView]]
  - [[Generating NSAttributedString from HTML]]

### Week 5 - UIKit Dynamics

We will be covering UIKit Dynamics and its associated behaviors like gravity, attachment, push, and snap. We will be covering topics and use cases such as the following:

- Basic dynamics
  - Applying behaviors like gravity to views
  - Handling callback for collision detection
  - Using rigid and flexible attachments
  - Applying continuous or instantaneous forces
  - Composing multiple behaviors
- Dynamics combined with Gestures and Animations
  - Dynamically adding or removing behaviors based on Gestures
  - Updating animator state when manually modifying view properties
  - Using view animation in conjunction with dynamics

#### Homework

The homework this week is to make an interactive mock of a simplified Paper "Edit Sections" page. Full homework description is [[here|Week 5 Homework]].

<img src="http://i.imgur.com/L0rQSqu.gif" width="250"/>&nbsp;&nbsp;<img src="http://i.imgur.com/qt4XhM8.gif" width="250"/>

#### Other links

- [[Week 5 Skills checklist|Designer Week 5 Skills Checklist]]
- Week 5 Quick References
  - [[Presenting Modal View Controllers]]
  - [[Working with UIKit Dynamics]]

### Week 7 - UICollectionView with UIKit Dynamics

We will be covering working with UICollectionView and integrating it with UIKit Dynamics. We will be covering topics and use cases such as the following:

- UICollectionView
  - Custom collection view cells
  - Using UICollectionViewFlowLayout for grid views
- UICollectionView with UIKit Dynamics
  - e.g., accordion scrolling in iMessages
  - e.g., menu in Paper

#### Homework

The homework this week is TBD. Full homework description is [[here|Week 7 Homework]].

#### Other links

- [[Week 7 Skills checklist|Designer Week 7 Skills Checklist]]
- Week 7 Quick References

### Week 8 - API design with Parse

We will be covering designing an API and implementation using Parse. We will be covering topics and use cases such as the following:

- Authentication
  - Signing in / Signing up
  - Accessing current user
- Schema
  - Designing basic models
  - Relationships
    - 1:1, 1:many, many:many
  - Queries
    - Using conditions
    - Eager loading related objects
  - Asynchronous saving / deleting