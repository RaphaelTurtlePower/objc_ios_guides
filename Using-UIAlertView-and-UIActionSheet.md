```
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:@"Title" message:@"This is the message!" delegate:self cancelButtonTitle:@"Cancel" otherButtonTitles:@"OK", nil];
[alertView show];
```

```
UIActionSheet *actionSheet = [[UIActionSheet alloc] initWithTitle:@"Title" delegate:self cancelButtonTitle:@"Cancel" destructiveButtonTitle:@"Delete" otherButtonTitles:@"OK", nil];
[actionSheet showInView:self.view];
```