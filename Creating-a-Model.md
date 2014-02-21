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

That's it for the basic declaration!

### Creating Models from Arrays and Dictionaries

Most APIs return their data in JSON arrays and dictionaries. For example, here's an excerpt of the data returned by Twitter.

```
{
  "id": 240558470661799936,
  "created_at": "Tue Aug 28 21:16:23 +0000 2012",
  "text": "I love sharing everything on Twitter",
  "user": {
    "id": 119476949,
    "name": "John Smith",
    "location": "San Francisco, CA",
    "url": "http://johnsmith.com",
    "profile_image_url_https": "https://si0.twimg.com/profile_images/730275945/john_happy.jpg",
  },
}
```

After receiving that JSON dictionary from Twitter, its convenient to be able to create your models directly from that dictionary. In addition, you'll commonly receive an array of dictionaries from the API, so it would be convenient if there were a method to create an array of Users from the array of dictionaries.

```
@interface User : NSObject

...

- (id)initWithDictionary:(NSDictionary *)dictionary;
+ (NSArray *)usersWithArray:(NSArray *)array;

@end
```

```
@implementation User

- (id)initWithDictionary:(NSDictionary *)dictionary {
  self = [super init];
  if (self) {
    self.name = dictionary[@"name"];
    self.profilePicUrl = dictionary[@"profile_image_url_https"];
    self.location = dictionary[@"location"];
  }

  return self;
}

+ (NSArray *)usersWithArray:(NSArray *)array {
    NSMutableArray *users = [[NSMutableArray alloc] init];
    
    for (NSDictionary *dictionary in array) {
        User *user = [[User alloc] initWithDictionary:dictionary];
        [users addObject:user];
    }
    
    return users;
}
@end
```

### Creating fake model data

If you're not connected to an API yet, its convenient to have a way to create fake data so you can test your views.

```
@interface User : NSObject

+ (NSArray *)fakeUsers;

@end
```

```
@implementation User

+ (NSArray *)fakeUsers {
  NSArray *fakeUserDictionaries = 
    @[
       @{ @"user": {
          @"id": @(119476949),
          @"name": @"John Smith",
          @"location": @"San Francisco, CA",
          @"url": @"http://johnsmith.com",
          @"profile_image_url_https": @"https://si0.twimg.com/profile_images/730275945/john_happy.jpg",
        },
       @{ @"user": {
          @"id": @(119476949),
          @"name": @"Jane Smith",
          @"location": @"San Francisco, CA",
          @"url": @"http://janesmith.com",
          @"profile_image_url_https": @"https://si0.twimg.com/profile_images/730275945/jane_happy.jpg",
        }
     ];

  return [User usersWithArray:fakeUserDictionaries];
}

@end
```
