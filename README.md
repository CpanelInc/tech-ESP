ESP - Enhanced Shell Prompt
===========================

Intro
----

ESP or Enhanced Shell Prompt is an bash prompt that contains various checks to help an tech know whats happening on the server.  Every time the PS1 prompt is rendered, checks for upcp, backups, easyapache, new SSH connections, and also service checks for apache, exim, mysql are run.  More checks will be introduced in future versions

Usage
-----

To use esp run the following command on Centos 5 or 6:

    source /dev/stdin <<< "$(curl -s https://raw2.github.com/cPanelTechs/ESP/master/esp)"

Special Thanks to Jerald Jonson for initially coding and hacking out the centos 5 bugs in the above source command that makes this tool possible, and his contributions to the ESP script itself.

Common Questions
----------------

### But theres already SSP ###

ESP is different that SSP in the fact that SSP runs an compressive set of checks on the initial login.  This tool, ESP runs checks constantly as an tech is working on the server to notify the tech of changing conditions on the server as they work as well as create alias, and bash functions for repetitive commands.

### What is checked ###

Currently the script will check for the following in the PS1 Alerts:
* If easyapache is running
* If upcp is running
* If backups are running
* If apache is down 
* If exim is down
* If MySQL is down
* If an new ssh connection/logout is detected

### What other features does ESP have ###

ESP has many features that can be useful besides being able to read minds.   ESP comes with an command cphelp that can be used to get more information on the commands available.

Credits
-------

Originally coded by Citizen Kepler, and contributions from Jerald Jonson (special thanks for the source command to call the script)
