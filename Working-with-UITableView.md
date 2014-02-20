Table views are the center of many iOS applications and have many features to customize their appearance and behavior. The sections below cover basic as well as more custom table views.

### Basic Table View

<img src="http://i.imgur.com/rYbUIR1.png" />

Download the sample code [here](https://github.com/thecodepath/ios_guides/tree/master/demos/SimpleTableView).

### Implementation

#### Step 1 - Create a view controller

Create a view controller with a xib, and drag a UITableView into the view, as shown below.

<img src="http://i.imgur.com/uDwEPMA.gif" />

#### Step 2 - Create a table view outlet

Control-drag from the nib to the implementation file to create an outlet to the UITableView, as shown below.

<img src="http://i.imgur.com/mkgZCJ2.gif" />

#### Step 3 - Set the datasource and delegate

In the header file, declare that the class implements the table view datasource and delegate protocols.

```
@interface MainViewController : UIViewController <UITableViewDataSource, UITableViewDelegate>
...
@end
```

In viewDidLoad, configure the datasource and delegate of the table view.

```
- (void)viewDidLoad
{
    [super viewDidLoad];

    self.tableView.dataSource = self;
    self.tableView.delegate = self;
}
```

#### Step 4 - Implement the table view methods

There are many table view methods, but the only required methods are to set the number of rows for the table view and to return the cell for each row.

```
#pragma mark - Table view methods

- (int)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section {
    return 5;
}

- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
    UITableViewCell *cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:nil];
    
    cell.textLabel.text = [NSString stringWithFormat:@"This is row %d", indexPath.row];
    
    return cell;
}
```



