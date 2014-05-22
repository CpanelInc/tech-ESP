ESP ChangeLog
============

May 22, 2014
------------
 * Fixed ccprpms command.

May 19, 2014 - v.0.05
---------------------
 * Added Peters acctinfo script
 * Renamed previous acctinfo script to acctinfo-marco
 * Created wo alias for  whoowns
 * Created ccrpms alias for check_cpanel_rpms
 * Added script CSI
 * Fixed and added back backup help section bug.
 * Updated methiod used to call ESP to use raw.githubusercontent.com
 * Updated scripts that used raw.github.com to raw.githubusercontent.com
 * Added Exim to the list of disabled checks for DNSOnly 



Mar 30, 2014 - v0.04
--------------------
 * case #36: cphelp - fixed typo in code that broke cphelp
 * case #37: Fix perdir which likely broke in 0.02
 * case #38: Increase the alertcheck timeout to 100
 * case #39: Wont implement at this time
 * case #40: The libkey check has a new url, so update the script to reflect this
 * case #41: Issues were seen on boxes with aliased `ps`, so always use `\ps`
 * case #42: Duplicate of case #41
 * Added Devlopment hooks. pre and post hooks called esp_hook_pre and esp_hook_post



Mar 11, 2014 - v0.03
--------------------
 * Updated run mode for DNS Only so that extra checks are skiped.
 * Added command for quickly looking up an accounts info (acctinfo) 
 * Added the command ips for an quick listing of just the IPS, one per line
 * Added configuration option for the Max no. of files that cl will list (Default=150) Option:  esp_cl_maxfiles
 * Added configuration option for enabling cl-on by default.   Issue [#31]
 * Added Migration Tools
 * Added timeout on the alert checks to prevent ESP from hanging the shell. DANGER ZONE!
 * Added configuration options to disable checks [#26]
 * Added DNS Only check
 * bke will now use vim and not vi


Feb 17, 2014 - v0.02
--------------
 * Implemented New configuration option system
 * Configuration option to call SSP automaticaly, however SSP is still disabled by default
 * Replaced history line number with the ticket number [#10]
 * Added checks to test if the mailserver process is dead
 * Addded check to check for cPanel and display 10 sec warning if cPanel is not detected [#13]
 * Added check for vim and sets that as the editor,  if vim is non-existant, it falls back to vi and creates an alias for vim to vi. [#22] 
 * Added a alert check for yum and also stale yum locks [#24]
 * Removed Grey color from $PS1 as it messes up some termanals [#12]
 * Updated sslhunter command to use the $DL_SCRIPTS var and be smarter when invoked. [#15]
 * Added universal script download and converted existing scripts to use the universal downloader [#18] [#15]
 * Updated easyapache check to also check for the EA touch file to reduice false positives
 * Added command fcrdns
 * Added command mysqltuner as an replacment for mysql tuner.  Useing MySQL tuning Primer Script from https://launchpad.net/mysql-tuning-primer/

Feb 9, 2014 - v0.01
-----------
 * Removed mysqltuner becuse it is out of date and is being pulled from cPanel in case 90317
 * Add Change Log [#16]

Feb 6, 2014
-----------
Inital Commits
