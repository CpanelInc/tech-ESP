ESP - Enhanced Shell Prompt
===========================

Intro 
----

ESP or Enhanced Shell Prompt is an bash prompt that contains various checks to help an tech know whats happening on the server.  Every time the PS1 prompt is rendered, checks for upcp, backups, easyapache, new SSH connections, and also service checks for yum locks, apache, exim, mysql are run.  More checks will be introduced in future versions

Usage
-----

To use esp run the following command on CentOS/CL 6 or 7:

# source /dev/stdin <<< "$(curl -sL https://esp.cpanel.xyz/esp)"

Special Thanks to Jerald Jonson for initially coding and hacking out the CentOS 5 bugs in the above source command that makes this tool possible, and his contributions to the ESP script itself.

This version is highly modified and updated by Terrance Robotham - This is maintained in a private git repository and is automatically uploaded to https://esp.cpanel.xyz/ automagically on a per-commit basis.

Configuration Options
---------------------

Configuration options in ESP are bash environment variables declared before the source command.  This allows configuration options to be set while not using any configuration files, and are easy to declare.  For example if we wanted to declare that we wanted to run SSP, we could set 'ssp=1' before the source command as shown below:

Example:

# ssp=1 source /dev/stdin <<< "$(curl -sL https://esp.cpanel.xyz/esp)"

### SSP 

You can enable SSP to run on script execution my declaring a bash environment variable called ssp before running the command for this script.  

Configuration Option: ssp

Options: '1' - Enable SSP, Default is disabled

### Default directory listing

As of esp 0.03 directory listings are now enabled by default, however this may not be desired for all servers or techs.  To disable this option, there is the following configuration option to disable this feature. 

esp_cl_disable

Any value to this varable will disable the cl feature and is only checked on the initial run. The command cl-off can be used after the initial run.

The second configuration option for the directory listing is the amount of files it will list.  By default this is 150, however it can be changed with the option esp_cl_maxfiles

esp_cl_maxfiles


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

#### cpsrvd

esp_check_disable_cpsrvd

#### Tailwatchd

esp_check_disable_tailwatchd

Common Questions
----------------

### But theres already SSP ###

ESP is different that SSP in the fact that SSP runs an compressive set of checks on the initial login.  This tool, ESP runs checks constantly as an tech is working on the server to notify the tech of changing conditions on the server as they work as well as create alias, and bash functions for repetitive commands.

### What is checked ###

Currently the script will check for the following in the PS1 Alerts:

* If EasyApache is running
* If upcp is running
* If backups are running
* If Apache is down 
* If Exim is down
* If MySQL is down
* If an new ssh connection/logout is detected
* If the mailserver is down
* If yum is running or has an stale lock

### What other features does ESP have ###

ESP has many features that can be useful besides being able to read minds. ESP comes with an command cphelp that can be used to get more information on the commands available.

Development Hooks
----------------

ESP features development hooks to allow for extra features and functions inside ESP without the need of forking the code and modifying ESP.  Hooks are relatively easy to use and can add a lot of custom functions to ESP.  To create an hook all you need to do is declare an bash function with the name of the hook.  Then when esp hits the hook it will test to see if the user has declared an hook and if so run it. 

### Pre-ESP Startup 

esp_hook_pre

This hook is run at the ESP startup, so if you wanted to run some code on ESP startup you can use this hook. This hook is not enclosed in safety timeouts, so if the command gets caught in an loop it will crash the shell.

#### Example of pre hook

An example of the pre hook could be to read ESP configuration options from a file.  ESP currently has no plans on developing this, however it has been requested.  A pre hook can be used to accomplish this.  In the following example we will declare an bash function and then load the configuration from inside this function/hook:

function esp_hook_pre { [ -f ~/.esprc ] && source ~/.esprc;};

Now you can run ESP and ESP will detect the hook and load ~/.esprc if it exists.  Additionally, you can combine the function, with configuration options and the ESP command for an (admittedly large) one liner. 

export esp_check_disable_mysql=1 function esp_hook_pre { [ -f ~/.esprc ] && source ~/.esprc;}; source /dev/stdin <<< "$(curl -sL https://esp.cpanel.xyz/esp)"

### Post-ESP hook 

esp_hook_post

Post hooks are useful for running code after ESP startup has completed. The post hook is the last thing run before ESP startup ends before dropping the user to the ESP shell.  This command is not run through the safety timeout system so if your hook gets caught in a loop it will crash the shell.

#### Example

An example of the ESP post hook is to modify the PS1 variable.  Like the pre hook we will be declaring an bash function with the hook name and placing the hook code inside the function:

function esp_hook_post { export PS1="$PS1 >>>"; };

Like the pre hook you can place the function before the esp command for an one liner:

function esp_hook_post { export PS1="$PS1 >>>"; }; source /dev/stdin <<< "$(curl -sL https://esp.cpanel.xyz/esp)"


Credits
-------

Originally coded by Citizen Kepler, and contributions from Jerald Jonson (special thanks for the source command to call the script)
