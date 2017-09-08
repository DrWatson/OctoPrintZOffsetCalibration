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
