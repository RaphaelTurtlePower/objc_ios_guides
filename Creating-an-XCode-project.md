There are a few new project templates in XCode, but it's best to start with the empty XCode project. The other project templates don't offer that much and for real projects, you end up having to delete a lot of things that the templates generate for you.

### Step 1: Creating a new empty project

Click on File->New->Project and create a new empty project.

<img src="http://i.imgur.com/tyZsMoL.png" width="731" height="494" />

### Step 2: Choose project options

<img src="http://i.imgur.com/lhcLWyY.png" width="731" />

- **Product Name** - The product name is just the name of your app, e.g., "Facebook", "Twitter", etc.
- **Organization Name** - This is the name of your company. This doesn't have to be a registered company, this can be any brand that you want to release your apps under.
- **Company Identifier** - This is always com.company, where company is the same value you used for organization.
- **Class Prefix** - This is optional and is more commonly set if you're making a library, not an app.
- **Devices** - This determines if your app is for the iPhone, iPad, or Universal. If you select iPhone, you can still run the app on an iPad, but it will show an iPhone frame within the iPad. If you select Universal, the app will expect different views for iPhone and iPad. If you submit an app to the store as an iPhone app, you can upgrade it later to Universal. If you submit an app as a Universal app, you can not downgrade it.

### Step 3: Running the project

<img src="http://i.imgur.com/auIzSuH.gif" width="375" height="207" />


