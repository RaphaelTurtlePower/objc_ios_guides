## Using UIRefreshControl

![Refresh|250](http://i.imgur.com/wRED0TT.gif)

Pull to refresh has been a standard UI convention in iOS since early days of Twitter. It's easy to include the default pull to refresh control into any scroll view, including UIScrollView, UITableView, or UICollectionView.

### Step 1: Create the UIRefreshControl

It's useful to create the UIRefreshControl as an instance variable at the top of the class because you need to access it to stop the loading behavior.

```
@interface MyViewController ()
@property (nonatomic, strong) UIRefreshControl *refreshControl;
@end

@implementation MyViewController
...
@end

```

### Step 2: Add the UIRefreshControl to the Scroll View

In `viewDidLoad`, add the refresh control as a subview of the scrollview (or tableview or collection view). It's best to insert it at the lowest index so that it appears behind all the views in the scrollview.

```
- (void)viewDidLoad {
    [super viewDidLoad];
    
    self.refreshControl = [[UIRefreshControl alloc] init];
    [self.refreshControl addTarget:self action:@selector(onRefresh) forControlEvents:UIControlEventValueChanged];
    [self.tableView insertSubview:self.refreshControl atIndex:0];
}

```

### Step 3: Implement the onRefresh Method

In Step 2 above, we said whenever the refreshControl changes state, it should call the `onRefresh` method. We need to define that method. When the refresh is complete, call endRefreshing on the refreshControl.

```
- (void)onRefresh {
    NSURL *url = [NSURL URLWithString:@"..."];
    NSURLRequest *request = [[NSURLRequest alloc] initWithURL:url];
    [NSURLConnection sendAsynchronousRequest:request queue:[NSOperationQueue mainQueue] completionHandler:^(NSURLResponse *response, NSData *data, NSError *connectionError) {
        
        [self.refreshControl endRefreshing];
    }];
}

```