ESP ChangeLog
============

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
