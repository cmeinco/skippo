splunk-kippo
============

SKIPPO for Kippo HoneyPot

<<<<<<< HEAD
# SKIPPO for Kippo HoneyPot


#### Version 0.1 Alpha

This app reads the database textlog output of the Kippo SSH HoneyPot.

Kippo is an SSH medium interaction honeypot, available at https://code.google.com/p/kippo/

Kippo-Graph is a script used to visualize Kippo statistics, available at http://bruteforce.gr/kippo-graph.  Kippo Graph visualizations were recreated as a dashboard within this app, the Kippo Graph script is not included.

## Installation

1. Setup Kippo, enable textlog
2. Configure inputs.conf to monitor kippo-textlog.log

## Configuration

1. Modify Kippo to enable textlog database log.
	[database_textlog]
	logfile = log/kippo-textlog.log
	
2. Add log monitor to inputs.conf (or use TA-kippo on remote kippo honeypot)
	[monitor:///opt/kippo/log/kippo-textlog.log]
	disabled = 0
	index = main
	sourcetype = kippo_textlog

## Support

Please open issues and provide feedback either through GitHub Issues or by contacting the team directly. 
http://answers.splunk.com/apps/ ? /related_questions/

## Contact Us

See https://code.google.com/p/splunk-kippo/

## License
Kippo App https://..../trentspeckhart (C) 2014

Kippo https://code.google.com/p/kippo/source/browse/trunk/doc/COPYRIGHT
Kippo-Graph https://github.com/ikoniaris/kippo-graph/blob/master/LICENSE.txt


#ICON CREATIVE COMMONS
openclipart.org/detail/176455/honeycomb-by-jesseakc-176455


## Future Ideas
* Pull in kippo configuration data
* Do basic malcode analysis, md5 against VT, etc
* Pull in tty logs
* align with Splunk CIM (Common Information Model)



## delete this

http://docs.splunk.com/Documentation/Splunk/latest/AdvancedDev/SetupExample1

[splunkbase requirements]
Important: If you plan to list your app or add-on on Splunkbase, you must ensure that the name of your app and references trademarks in related materials (such as marketing literature and documentation) meet the requirements specified in "Naming conventions for content on Splunk Apps" in the Working with Splunk Apps Manual.

Before you package your app or add-on, make sure you have all the components and that they work:

1. If you have not already done so, create a dedicated directory for your app or add-on under $SPLUNK_HOME/etc/apps/ (for example: $SPLUNK_HOME/etc/apps/<app_name>). If you created an app using app builder, this has been created for you. This directory is denoted by $APP_HOME for the rest of this topic.

2. Create or edit your $APP_HOME/default/app.conf file. If you created an app using app builder, app.conf has been created for you but you still need to add a stanza to have a description of your app show up in Launcher. If you are packaging an add-on, you need to create your app.conf file.

3. Review the app.conf.spec documentation to ensure your app can be uploaded to Splunkbase.

Splunkbase requires an App ID, version string, and a description defined in app.conf.
By default, Splunk checks for updates to an app. If you do not want Splunk to check for updates, include the following in app.conf:
[package] 
check_for_updates = 0
Splunkbase validates app.conf and other app files and does not allow you to upload if there are errors.
4. If you want an icon or screenshot on Splunkbase or in the Launcher, create an icon and put it in $APP_HOME/appserver/static. If you are packaging an app, you can create a screenshot and place it in the same location. See Files and directories for apps and add-ons for requirements.

5. Place any scripts in the $APP_HOME/bin directory and make sure $APP_HOME/default/inputs.conf is set up correctly. If your app or add-on includes scripted inputs, scripted searches, or scripted lookups, you should follow general best practices for writing and testing the scripts. For example:

Include any dependencies your app or add-on needs to run outside of your environment. You may want to test it on a different system to make sure it works out of the box.
Splunk recommends that you make sure fields, event types, or other information tags adhere to the Splunk Common Information Model Add-on. This ensures that your app works with other Splunk instances.
Scripts that serve their own webpage and need a new REST endpoint must be specified in restmap.conf.
On *nix platforms, you can use environment variables to set locations in any scripts within your app or add-on so that they only have to be set once. If you do so, make sure to include this information in your README.txt.
(Optional) Write a setup screen to allow your users to configure local settings.
Provide instructions to test your scripts outside of Splunk.
If your app is intended to run cross-platform, include both .sh and .bat files for scripted inputs and include an inputs.conf that can enable either one. You can enable both options by default (only one will run), write a setup script to allow the user which option to enable, or give the user manual instructions on how to enable the option they want. An example with both input types enabled:
[script://./bin/my_input.sh]
interval = 60
sourcetype = my_sourcetype
disabled = 0

[script://.\bin\my_input.bat]
interval = 60
sourcetype = my_sourcetype
disabled = 0
6. Make sure you have the correct configuration files, views, and navigations for your app or add-on. Objects created prior to the development of the app or add-on may be in $SPLUNK_HOME/etc/apps/search/local or $SPLUNK_HOME/etc/system/local. For example, if you are packaging field extractions, they may be defined in stanzas in props.conf and/or transforms.conf in the Search app. Wherever you make use of a stanza in a .conf file, you need to:

(a) create a blank version of each relevant .conf file in your $APP_HOME/default directory.

(b) copy the stanza heading and the relevant lines from the original .conf file to the version in $APP_HOME/default. Do not copy lines or stanzas that are not directly relevant to your app.

Where it's hiding	 Move to
$SPLUNK_HOME/etc/system/local/  	 $APP_HOME/default/
$SPLUNK_HOME/etc/apps/search/local/  	 $APP_HOME/default/
$SPLUNK_HOME/etc/users/admin/<app_name>/	 $APP_HOME/default/
$APP_HOME/metadata/local.meta	 $APP_HOME/metadata/default.meta
See Files and directories for apps and add-ons for the correct file structure you need to share an app.

See About configuration files for an overview of Splunk configuration files, and a list and description of all configuration files.


7. Verify permissions for each object in your app or add-on and change any permissions that aren't set correctly. You can set permissions using Splunk Manager or by editing default.meta. If you are creating an add-on that is not Visible, you must make each object globally available. For a general overview of setting permissions, see Manage knowledge object permissions in the Knowledge Manager manual. For instructions on setting app permissions, see Step 5: set permissions in the Developer manual. If you set permissions through Manager, make sure that the permissions end up in default.meta and not local.meta.

8. Validate the XML for your views and navigation by running validate_all.py. See Use XML Schemas in this manual for more information.

9. Document your app. You can distribute your documentation in any of the following ways:

A README.txt file in your $APP_HOME directory
Documentation directly on your Splunkbase page. We recommend you document your app or add-on first and then cut and paste the documentation into the Splunkbase page.
A PDF file in $APP_HOME/appserver/static/
10. If your app needs user-supplied information (for example, an app that requires a Twitter account to analyze Twitter data), make sure to remove the information for your test account before tarring the final version.

11. Tar and zip your app as described in the next section.

12. Test your package.

Extract your package in a clean Splunk install in a different location and environment than the one where you built your app or add-on.
Log in as a different Splunk user from the one you used to create the app.
You may also want to test it with earlier versions of Splunk.


Packaging your app for Splunkbase
The final step before uploading your app to Splunkbase is packaging. This means taking your app's directory and turning it into a single compressed file which can be uploaded to Splunkbase.

Splunkbase uploads are required to have the .spl file extension, e.g. myapp.spl. SPL format is identical to .tar.gz format (also known as a "tarball"). The only difference is the file extension.

Make sure you have placed all the app's components in the correct location, have moved all customizations from /local to /default, and have tested your app before you package it.

You can use your preferred file-compression utility to create the .tar.gz-format file, or you can follow the OS-specific instructions below.

Packaging on Unix/Linux/Mac
On Linux/Unix systems, creating a .tar.gz is straightforward because tools for creating .tar.gz archives are packaged with almost all *nix OS distributions. First you need to tar your app's folder, which creates a .tar file. Then you need to gzip the folder into a .tar.gz file. Finally, rename the file extension from .tar.gz to .spl.

Packaging on Mac
On Mac OS X, use gnutar rather than the default tar packaged with the OS. The default tar utility generates a series of warnings that can be problematic when packaging your app.

For example, you can do the following:

alias tar='gnutar'

For Mac OS 10.5 and later, set the environment variable COPYFILE_DISABLE before using tar to avoid unwanted metadata files being added to your .spl file, which may cause your upload to fail. For earlier versions of OS X, set COPY_EXTENDED_ATTRIBUTES_DISABLED.

$ export COPYFILE_DISABLE=true

Example packaging commands
$: tar cv appdirpath/ > appname.tar 
$: gzip appname.tar 
$: mv appname.tar.gz appname.spl




=======
>>>>>>> 00d6c6da0af86c6fedd4c631ac9ca99b651303bb
