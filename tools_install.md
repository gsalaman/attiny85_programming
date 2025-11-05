# Installing tools to program ATTINY 85

First, you need the old version of arduino....NOT one of the 2.x versions that say "IDE".  You can get it from here:

https://www.arduino.cc/en/software/#previous

About half way down, you'll see "legacy IDE".  Use that...it should be a 1.x Version rather than a 2.x version.

This will give you a zip file...unzip somewhere on your HD and run arduino.exe

Next, you need to add a boards manager location.  Open preferences, and in "additional board url", paste the following:

https://raw.githubusercontent.com/damellis/attiny/ide-1.6.x-boards-manager/package_damellis_attiny_index.json

Then, go to tools->boards->board manager, and type tiny in the search box.  That should bring up the attiny board library by David Mellis.  Install that.

Now, you can select the following under boards:
