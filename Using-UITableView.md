## Overview

Table views are the center of many iOS applications and have many features to customize their appearance and behavior. The sections below cover basic as well as more custom table views.

<img src="http://i.imgur.com/rYbUIR1.png" />

Download the sample code [here](https://github.com/thecodepath/ios_guides/tree/master/demos/SimpleTableView).

### Basic Table View

#### Step 1: Create a view controller

Create a view controller with a xib, and drag a UITableView into the view, as shown below.

<img src="http://i.imgur.com/uDwEPMA.gif" />

#### Step 2: Create a table view outlet

Control-drag from the nib to the implementation file to create an outlet to the UITableView, as shown below.

<img src="http://i.imgur.com/mkgZCJ2.gif" />

#### Step 3: Set the datasource and delegate

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

#### Step 4: Implement the table view methods

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

### Table View with Custom Cells

In practice, a UITableViewCell is rarely appropriate for your table views. Instead, you'll often need to create a custom cell with different subviews and custom highlight and selection effects. To create and use a custom cell, follow the steps below.

#### Step 1: Define the custom cell

The video below demonstrates the process of creating a custom cell using XCode 5.1.

<iframe src="//player.vimeo.com/video/89248377" width="500" height="375" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

#### Step 2: Register the cell

```
- (void)viewDidLoad {
   [super viewDidLoad];
   UINib *movieCellNib = [UINib nibWithNibName:@"YourCustomCell" bundle:nil];
   [self.tableView registerNib:movieCellNib forCellReuseIdentifier:@"YourCustomCell"];
}
```

#### Step 3: Dequeue the cell

```
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
   YourCustomCell *cell = [tableView dequeueReusableCellWithIdentifier:@"YourCustomCell" forIndexPath:indexPath];

   return cell;
}
```