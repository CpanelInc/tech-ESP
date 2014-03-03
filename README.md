ESP - Enhanced Shell Prompt
===========================

Intro
----

ESP or Enhanced Shell Prompt is an bash prompt that contains various checks to help an tech know whats happening on the server.  Every time the PS1 prompt is rendered, checks for upcp, backups, easyapache, new SSH connections, and also service checks for yum locks, apache, exim, mysql are run.  More checks will be introduced in future versions

Usage
-----

To use esp run the following command on Centos 5 or 6:

    # source /dev/stdin <<< "$(curl -sL https://raw.github.com/cPanelTechs/ESP/master/esp)"

Special Thanks to Jerald Jonson for initially coding and hacking out the centos 5 bugs in the above source command that makes this tool possible, and his contributions to the ESP script itself.

Configuration Options
---------------------

Configuration options in ESP are bash envirmentals declared before the source command.  This allows configuration options to be set while not using any configuration files, and are easy to declare.  For example if we wanted to declare that we wanted to run SSP, we could set 'ssp=1' before the source command as shown below:

Example:

    # ssp=1 source /dev/stdin <<< "$(curl -sL https://raw.github.com/cPanelTechs/ESP/master/esp)"

### SSP 

You can enable SSP to run on script execution my declaring an bash envermental called ssp before running the command for this script.  

Configuration Option: ssp

Options: '1' - Enable SSP, Default is disabled

### Dirtectory Listing when entering an directory

ESP can list the contents of an directory when you enter it by useing the command 'cl-on' however to have this set and enabled by default you can use the following configuration option

    cl=1


### Disable Checks

ESP checks can be disabled individually or all of them can be disabled at once.  The checks are disabled by declaring the following variables before the source command or with export once ESP has been run.

#### Disable all checks

    esp_check_disable_all

#### UPCP

    esp_check_disable_yum

#### Backups

    esp_check_disable_backup

#### EasyApache

    esp_check_disable_easyapache

#### Apache

    esp_check_disable_apache

#### Exim

    esp_check_disable_apache

#### MySQL

    esp_check_disable_mysql

#### Mailserver

     esp_check_disable_mailserver

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
* If the mailserver is down
* If yum is running or has an stale lock

### What other features does ESP have ###

ESP has many features that can be useful besides being able to read minds.   ESP comes with an command cphelp that can be used to get more information on the commands available.

Credits
-------

Originally coded by Citizen Kepler, and contributions from Jerald Jonson (special thanks for the source command to call the script)
