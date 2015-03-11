splunk-kippo
============

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



