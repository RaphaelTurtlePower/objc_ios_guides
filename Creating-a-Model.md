Every application has models to represent its data types. For example, Twitter has Users, Tweets, Followers, and Lists. Facebook has Users, Posts, Friends, Likes, and Comments. Each model, like a User, is simply a collection of properties. For example, a User might consist of name, profile picture, and birthday. In mobile applications, models are very simple because most of the business logic lives in the cloud. One of its primary responsibilities is simply to define the properties.

### Creating a Model

To create a model class for User, create a new class that inherits from NSObject and declare its properties.

```
@interface User : NSObject

@property (nonatomic, strong) NSString *name;
@property (nonatomic, strong) NSString *profilePicUrl;
@property (nonatomic, strong) NSString *location;

@end
```

The implementation is empty because the properties are automatically synthesized.

```
@implementation User

// Nothing goes here!

@end
```