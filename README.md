# Delete Facebook Group Posts in 2017

![Image of Delete Facebook Group Posts](https://raw.githubusercontent.com/cefjoeii/delete-fb-group-posts/master/delete-fb-group-posts.png)

The one that initially worked is through the **mbasic** mode. I tried making a script for the **desktop** and **mobile** version of Facebook at first but the delete buttons generate unpredictable POS values when not refreshed. I encountered some glitches with mbasic along the way so I knew I had to make the desktop hack work.

So let's go and clean that spam-infested Facebook group of yours.

#### Step 1
Download the  [_iMacros for Chrome_](https://chrome.google.com/webstore/detail/imacros-for-chrome/cplklnmnlbnpmjogncfgfijoopmnlemp?hl=en) extension.

#### Step 2
The extensions can be seen at the top right corner of the browser. Click on the _iMacros for Chrome_ icon to run.

#### Step 3
Go to the **Record** tab just below the yellowish tree pane.

#### Step 4
For **mbasic.facebook.com**,

Click on the **Record Macro** button then click on the **Stop** button. The iMacros Editor will pop out.

Replace the code inside the editor with:

```javascript
SET !TIMEOUT_STEP 1
SET !ERRORIGNORE YES

WAIT SECONDS=3

TAG POS=1 TYPE=SPAN ATTR=TXT:See<SP>More<SP>Posts
WAIT SECONDS=3

TAG POS=1 TYPE=A ATTR=TXT:*Comment*
WAIT SECONDS=3

TAG POS=1 TYPE=A ATTR=TXT:Delete
WAIT SECONDS=3

TAG POS=1 TYPE=INPUT:SUBMIT FORM=ACTION:/a/delete.php?* ATTR=*
WAIT SECONDS=4
```

Hit **Save As & Close** button. Rename the script to something like **mbasic.iim** Make sure you got that extension correctly.


#### Step 5
For **www.facebook.com**,

Click on the **Record Macro** button again then click on the **Stop** button.

Replace the code inside the editor with:

```javascript
SET !TIMEOUT_STEP 1
SET !ERRORIGNORE YES

URL GOTO=https://www.facebook.com/groups/URL
WAIT SECONDS=3

TAG POS=2 TYPE=A ATTR=ID:u_0_2*
WAIT SECONDS=2

TAG POS=1 TYPE=SPAN ATTR=TXT:Delete<SP>File
WAIT SECONDS=2

TAG POS=1 TYPE=SPAN ATTR=TXT:Delete<SP>Post
WAIT SECONDS=2

TAG POS=1 TYPE=BUTTON ATTR=TXT:Delete
WAIT SECONDS=2
```

As you can see from the code, there is a URL. Change it to your group's URL

Hit **Save As & Close** button. Rename the script to something like **www.iim** Make sure you got that extension correctly as well.

#### Step 6
Go to the **Play** tab. Set the Max value to 999.

#### Step 7
Go to your facebook group's url and make sure your language is set to English.
Example: mbasic.facebook.com/groups/URL or www.facebook.com/groups/URL

#### Step 8
Select the appropriate script from the yellowish tree pane.

Hit the **Play Loop** button. See the magic happens.

### If this worked for you, you're free to hit the Star button.

<br>

## Code Explained

#### I just learned this iMacros scripting and I think it might be worth the share. My script is still running and deleting posts at the time of writing this.

<br>

`SET !TIMEOUT_STEP n` This is probably for the error timeout.

`SET !ERRORIGNORE YES` Ignore any errors so the loop continues. Part of my debugging process.

`WAIT SECONDS=n` Change your waiting time if you have a slower connection or computer.

<br>

For **mbasic**,

`TAG POS=1 TYPE=SPAN ATTR=TXT:See<SP>More<SP>Posts` Sometimes, mbasic hides all the remaining old posts.

`TAG POS=1 TYPE=A ATTR=TXT:*Comment*` Select the first `<a>` element that contains the string 'Comment'.

`TAG POS=1 TYPE=A ATTR=TXT:Delete` Select the `<a>` element that contains the string 'Delete'.

`TAG POS=1 TYPE=INPUT:SUBMIT FORM=ACTION:/a/delete.php?* ATTR=*` Select the submit button. This one is tricky. I replaced the long url thing after the `.php?` with a wildcard `*` to make the script work on every iteration of the loop.

<br>

For **www**,

`URL GOTO=https://www.facebook.com/groups/URL` This refreshes the page to ensure that we are selecting the right first or second element every time.

`TAG POS=2 TYPE=A ATTR=ID:u_0_2*` Select the `<a>` element with the id attribute that starts with u_0_2.There is a post that can't be deleted so I tried to skip it by setting the value of POS to 2. Tweak this if you need to.

`TAG POS=1 TYPE=SPAN ATTR=TXT:Delete<SP>File` Sometimes a "Delete Post" button appears as "Delete File". In any case, the script will go through this.

`TAG POS=1 TYPE=SPAN ATTR=TXT:Delete<SP>Post` If there is no such button as "Delete File", this comes to rescue.

`TAG POS=1 TYPE=BUTTON ATTR=TXT:Delete` You get the point.

Thanks! That's a lot of http requests for you!
