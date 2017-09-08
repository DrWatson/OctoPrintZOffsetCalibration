# OctoPrintZOffsetCalibration
Custom buttons and scripts for OctoPrint to allow for easier calibration of the Z Offset using a touch sensor.

The files here are provided AS IS. Altering your OctoPrint configuration using these instructions and code is done at your own risk.

I tried to make this a little easier using the available PlugIn framework of Octoprint, but due to some limits in the framework, you cannot inject feedback style custom controls using a JS script. Although this may be a feature available in future versions of OctoPrint, I didn't want to wait for that.

To make use of this functionality, you need to do two things:
1) Edit your config.yaml file
2) Create a folder structure and put the CalibrateExtruder file in it.

Instructions:
-------------
Updating the config.yaml File
-----------------------------
1) Download config.yaml and CalibrateExtruder from this repo.
2) Locate your config.yaml file on your OctoPrint deployment. It's usually in ~pi/.octoprint. 
3) Make a backup of config.yaml. 
4) Open your config.yaml in your editor of choice.
5) Look for a section named "controls:". It may not be there if you don't have any custom controls added.
6) If you DON'T have that section, then go to the bottom of the file and paste the entire contents of the config.yaml file found in this repo and save the file. Go to the next section called "Installing the CalibrateExtruder File".
7) If you DID find that section, open the config.yaml file from this repo and remove the first line "controls:"
8) Copy the contents of this file and paste it immediately under the "controls:" line in your config.yaml file. Save the file.

Installing the CalibrateExtruder File
-------------------------------------
1) Create the directory structure ~/.octoprint/scripts/gcode/custom
2) Copy the CalibrateExtruder file to the above directory.

Completing the Installation
---------------------------
1) Restart OctoPrint

How to Use the Utility
----------------------
On the Control tab in OctoPrint, you should see a section named Z Offset Calibration. In this section are two lines. The first line is an input box allowing you to specify what you would like to set as your Z Offset to EEPROM. Not sure what to set it to? That's where the second line of controls comes in. Click the "Query For Current Offset" button. Following this click, your current offset will be shown next to the button. You can then use this value as your starting point to fine tune the Z Offset.

Enter in your corrected value into the Z Offset text box and click the "Set and Test" button.

If your input is not within range (between -4 and 4 by default) it will cause the print head to jitter back and forth a tiny amount to indicate an error. If your input is not found to be numeric, the same jitter will occur.

If the input passes the above validation the following steps will be performed:
1) The value will be saved to to EEPROM
2) X, Y and Z will be homed
3) An auto level sequence will be performed
4) The bed and head will be centred (NOTE: The actual coordinates of the head will be placed at X60 Y111. Edit line 7 of CalibrateExtruder if you would rather have the head go to a different spot for testing.)
5) The Z axis will be set to zero height

After this is complete, test with a piece of paper for distance between nozzle and bed. Repeat steps adjusting Z offset as required.

It is recommended to heat up the hot end and print bed to compensate for thermal expansion that affects calibration.
You should also clean the nozzle tip removing any left over filament so it's not in the way during calibration and testing.
