# ff-kactivities
Script to create a Firefox profile and link it to the current Plasma Activity.

### Introduction

You may know that when you stop an Activity some opened apps can "hibernate", they free RAM but when you restart the Activity they reappear in the same state (Dolphin at the same path, Kate and Okular with the same documents etc) and the same size and position on the screen. This generally works for KDE applications. But at the moment KDE misses a good web browser and so I use Firefox.

Mozilla's browser has an option to automatically restore the previous session (tabs) when you start it. I use this feature a lot but sometimes I want to keep a session "saved" while I open a new one for another task (work vs study vs entertainment etc). This is why I tried to combine Firefox's profiles (each one has its own "session") with Plasma Activities.

I ff-kactivities that copies the "default" Firefox profile (with history, addons, settings, everything) into the same folder with a new name, create an entry in the app menu and link it to the current Activity. So if you set you desktop to show the files linked to current Activities (or if you set a folder view [as explained here](http://www.alexl.netsons.org/blogposts/plasma-tricks-different-app-menu-for-different-activities/) to make a by-activity app menu) you will get a different Firefox launcher for each Activity.

Just run the script and it will ask you a name to let you identify the launcher, for example if you reply "Study" the launcher will be "Firefox (Study)".

The following image show a folder view plasmoid set to show *.desktop files linked to the current Activity:

![](http://www.alexl.netsons.org/wp-content/uploads/2017/07/17-07-05-1804.png)

### Start the script using the right click menu on Firefox launcher

If you want a quick entry to start the script, I suggest you to edit the Firefox launcher in `~/.local/share/applications` with an action as in the following image:

![](http://www.alexl.netsons.org/wp-content/uploads/2017/07/17-07-05-1803.png)

You have to add to firefox.desktop the follow:

```
Actions=Activity

[Desktop Action Activity]
Exec=path/to/the/script/ff-kactivities
Icon=list-add-user
Name=New profile for current Activity
```

### Warnings

Before using the script, be sure that there is firefox.desktop in `~/.local/share/applications` and Firefox stores profiles in `~/.mozilla/firefox`. If not, edit the script to use the right paths for your system.

Also: don't exaggerate with Firefox profiles because each of the is approximately hundred megabytes.

I didn't add any way to delete the profiles, just go to `~/.mozilla/firefox` and manually delete them. And manually delete the entries in `~/.local/share/applications`.

If you restart the script in an Activity that already has a profile linked it will be overwritten.

I hope this could help you as it does for my workflow.
