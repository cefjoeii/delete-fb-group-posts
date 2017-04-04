# Delete Facebook Group Posts in 2017

![Image of Delete Facebook Group Posts](https://raw.githubusercontent.com/cefjoeii/delete-fb-group-posts/master/delete-fb-group-posts.png)

The one that worked is through the **mbasic** mode. I tried making a script for the **desktop** and **mobile** version of Facebook but the delete buttons generate unpredictable POS values. So let's go and clean that spam-infested Facebook group of yours.

#### Step 1
Download the  [_iMacros for Chrome_](https://chrome.google.com/webstore/detail/imacros-for-chrome/cplklnmnlbnpmjogncfgfijoopmnlemp?hl=en) extension.

#### Step 2
The extensions can be seen at the top right corner of the browser. Click on the _iMacros for Chrome_ icon to run.

#### Step 3
Go to the **Record** tab just below the yellowish tree pane.

#### Step 4
Click on the **Record Macro** button then click on the **Stop** button. The iMacros Editor will pop out.

#### Step 5
Replace the code inside the editor with this one:

```
SET !TIMEOUT_STEP 1
SET !ERRORIGNORE YES

TAG POS=1 TYPE=A ATTR=TXT:*Comment*
WAIT SECONDS=1

TAG POS=1 TYPE=A ATTR=TXT:Delete
WAIT SECONDS=1

TAG POS=1 TYPE=INPUT:SUBMIT FORM=ACTION:/a/delete.php?* ATTR=*
WAIT SECONDS=3
```

#### Step 6
Hit **Save As & Close** button. Rename the script to something like **delete-fb-group-posts.iim** Make sure you got that extension correctly.

#### Step 7
Go to the **Play** tab. Set the Max value to 999.

#### Step 8
Go to your facebook group's url and make sure your language is set to English.
Example: mbasic.facebook.com/groups/_group-url_

#### Step 9
Hit the **Play Loop** button. See the magic happens.

### If this worked for you, you're free to hit the Star button.

<br>

## Code Explained

<br>

#### I learned this iMacros scripting just today and I think it might be worth the share.

`SET !TIMEOUT_STEP n` The elements of the page won't load immediately at times. Tweak this if you want.

`SET !ERRORIGNORE YES` Ignore any errors so the loop continues. Part of my debugging process.

`TAG POS=1 TYPE=A ATTR=TXT:*Comment*` Select the first `<a>` element that contains the string 'Comment'.

`WAIT SECONDS=n` Change your waiting time if you have a slow connection or computer.

`TAG POS=1 TYPE=A ATTR=TXT:Delete` Select the `<a>` element that contains the string 'Delete'.

`TAG POS=1 TYPE=INPUT:SUBMIT FORM=ACTION:/a/delete.php?* ATTR=*` Select the submit button. This one is tricky. I replaced the long url thing after the `.php?` with a wildcard `*` to make the script work on every iteration of the loop.

Thanks.
