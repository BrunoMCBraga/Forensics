
# OSX Artifacts

Some artifacts may not be present on all OSX versions.

## OSX relevant directories
* /Applications
* /System (e.g. system libraries, configurations)
* /Volumes (e.g. mounted volumes, DMGs)
* /Network (e.g. network devices, servers)
* /Library (e.g. shared libraries, settings, preferences)
* /Users (user accounts)
* /bin (e.g. common binaries)
* /sbin (e.g. administrative tools)
* /usr (e.g. e.g. libraries, binaries, configuration files)
* /var (symbolic link to /private/var. Contains files generated and modified through execution of the OS)
* /etc (e.g. system configurations, administrative files)
* /dev (peripheral devices)
* /tmp (temporary files)
* /opt (not widely used but should hold optional software and packages)
* /.vol (pseudo-directory is used to access files by their ID number (aka inode number))
* /.Trashes (files and folders from boot volume)



## Installs And Updates
* /Library/Preferences/com.apple.SoftwareUpdate.plist (updates)
* /Library/Receipts/InstallHistory.plist and /private/var/log/install.log (software installatiom history)
* /var/db/receipts/, /private/var/db/recipts/ (BOM files)
* /Applications/[Application].app/Contents/_MASReceipt/receipt (BOM files for application)
* /private/var/log/install.log (only applications installed through packages)

## Network, Wireless, Bluetooth
* /private/var/db/dhcpclient/leases/ (dhcp leases)
* /etc/hosts (mapping hostname, IP)
* /Library/Preferences/SystemConfiguration/com.apple.airport.preferences.plist
* /Library/Preferences/SystemConfiguration/com.apple.network.identification.plist (OSX <10.9) 
* /Library/Preferences/com.apple.Bluetooth.plist (paired devices)
* /Library/Preferences/com.apple.alf.plist (application level firewall)
* /etc/pf.conf (Packet Filter configuration)
* /var/log/appfirewall.log (firewall logs)
* /private/var/db/launchd.db/com.apple.launchd/overrides.plist 
* /Library/Preferences/com.apple.alf.plist
* /Library/Preferences/com.apple.VNCSettings.txt (screen sharing password)
* /Library/Preferences/com.apple.RemoteManagement.plist (remote management configuration)
* /Library/Preferences/com.apple.filesharingui.plist (file sharing)

## GUI
* ~/Library/Preferences/com.apple.finder.plist (e.g. volumes and recent files)
* ~/Library/Preferences/com.apple.sidebarlists.plist
* ~/Library/Application Support/com.apple.sharedfilelist/com.appleLSSharedFileList.FavoriteServers.sfl
* ~/Library/Preferences/com.apple.dock.plist
* ~/Library/Preferences/com.apple.desktop.plist 
* ~/Library/Application Support/Dock/desktoppicture.db
* ~/Library/Preferences/com.apple.spaces.plist
* ~/Library/Saved Application State/<Bundle ID>.savedState ~/Library/Containers/<BundleID>/Data/Library/Saved Application State/
* ~/Library/Preferences/com.apple.spotlight.plist
* ~/Library/Application Support/com.apple.spotlight.Shortcuts.plist 

## Recent folders, executed applications and volumes
* ~/Library/Preferences/com.apple.finder.plist
* ~/Library/Preferences/com.apple.DiskUtility.plist
* ~/Library/Logs/DiskUtility.log
* ~/Library/Logs/fsck_hfs.log or ~/Library/Logs/fsck_apfs.log (HFS and APFS file system check log)
For <10.10:
* ~/Library/Preferences/com.developer.app.LSSharedFileList.plist (e.g. recent documents per application.)
* ~/Library/Preferences/com.apple.recentitems.plist (e.g. applications, documents, servers, hosts. Works for <10.10)
For >10.11
* ~/Library/Application Support/com.apple.sharedfilelist/.*sfl (recent files and other interesting artifacts. Works for >10.11)
* ~/Library/Preferences/com.apple.finder.plist (recent folders)
* Query spotlight metadata using **mdls**,. The relevant attributes are kMDItemLastUsedDate, kMDItemUsedDates and kMDItemUseCount.
These values are updated by LaunchServices upon doubl-eclicking or when an application opens another file through LaunchServices.
* ~/Library/Application Support/CrashReporter and /Library/Logs/DiagnosticReports (crash dumps for applications)
* /var/db/systemstats/snapshots.db (tracks power usage for applications)
* /.Spotlight-V100/VolumeConfiguration.plist 

## Services, daemons, kernel extensions and login items
* [APPLICATION_BUNDLE]/Contents/XPCServices/, /System/Library/XPCServices/
* /Library/LaunchDaemons, /System/Library/LaunchDaemons
* /Library/LaunchAgents, ~/Library/LaunchAgents 
* /System/Library/LaunchAgents
* /System/Library/Extensions, /Library/Extensions
* ~/Library/Preferences/com.apple.loginitems.plist, /Applications/<application>.app/Contents/Library/Log inItems/, /Library/Preferences/com.apple.loginitems.plist (login items)
* /System/Library/StartupItems, /Library/StartupItems (created based on StartupParameters.plist inside App folder)
* /etc/crontab, /var/at/tabs/[USERNAME] (cron jobs for system and user)

## Accounts
* /Library/Preferences/com.apple.preferences.accounts.plist (deleter users)
* /Library/Preferences/com.apple.loginwindow.plist (e.g. last connected user, whether there is a autologin user, password for autologin)
* /private/var/db/dslocal/nodes/Default/users/[username].plist (information about users)
* /private/var/db/dslocal/nodes/Default/groups/[groupname].plist (information about groups)
* ~/Library/Accounts/Accounts3.sqlite (e.g. Mail.app, Messages, Social Media)
* /private/var/db/dslocal/nodes/Default/users (users information for ACL purposes)
* /private/var/db/dslocal/nodes/Default/groups (groups information for ACL purposes)

## Applications

### Mail.app
* ~/Library/Mail/V3/ (e.g. .emlx, .mbox files)
* ~/Library/Mail/V3/MailData (e.g. email rules, account information)
* ~/Library/Containers/com.apple.mail/Data/Library/Mail Downloads/
* ~/Library/Caches/com.apple.mail/Cache.db
* ~/Library/Containers/com.apple.mail/Data/Library/Caches/com.apple.mail/Cache.db
* ~/Library/Containers/com.apple.mail/Data/Library/Preferences/com.apple.mail.plist (e.g. mail searches through spothlight)
 
### Microsoft Office
* ~Library/Preferences/com.microsoft.office.plist (2011 MRUs)
* ~/Library/Containers/com.microsoft.<app>/Data/Library/Preferences/com.microsoft.<app>.securebookmarks.plist (2016 MRUs)

### Save Application State
* ~/Library/Containers/<bundle‐ ID>/Data/Library/Saved Application State/ (windows.plist contains information about windows that should be opened when the application is executed)

### Microsoft Remote Desktop
* ~/Library/Containers/com.microsoft.rdc.mac /Data/Library/Application Support/Microsoft Remote Desktop/logs/rdplog.log
* ~/Documents/RDC Connections/ (inspect default.rdp files)

### Firefox
* ~/Library/Application Mozilla Firefox Support/Firefox/Profiles/[RANDOM].default/*.sqlite

### Chrome
* ~/Library/Application Support/Google/Chrome/Default/*

### Safari
* ~/Library/Safari/*.plist


### Shell History
* ~/.sh_history (Korn shell)
* ~/.bash_history (Bash)
* ~/.zsh_history/, ~/.zhistory, ~./history (Zshell. If none of those work, check ~/.zshrc for the location of the file).
* ~/.bash_sessions/<GUID>.history (>10.11)
* /var/root/[ONE_OF_THE_ABOVE]

## Backups
* /Library/Preferences/com.apple.TimeMachine.plist
* /var/db/com.apple.TimeMachine.SnapshotDates.plist
* /var/log/system.log

## Printing
* /var/log/cups/page_log (e.g. printing job names)
* /var/log/cups/access_log (e.g. printers used)
* /private/var/spool/cups (printing jobs. Can be parsed using cups_control from http://jafat.sourceforge.net/)
* /etc/cups/printers.conf, /Library/Preferences/org.cups.printers.plist (configured printers)
* /private/var/log/cups/error_log 

## Misc
* ~/Downloads (user downloads)
* ~/.ssh/known_hosts (hostnames, IPs and keys for SSH sessions)
* ~/Library/Application Support/Screen Sharing/*.vncloc (<10.10)
* ~/Library/Containers/com.apple.ScreenSharing/Data/Library/Application Support/Screen Sharing/*.vncloc (>10.11)
* File Quarantine (for files downloaded from the internet):
 * /Library/Containers/<bundle_id>/Data/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV2 (10.11)
 * ~/Library/Preferences/com.apple.LaunchServices.QuarantineEvents
 * ~/Library/Preferences/com.apple.LaunchServices.QuarantineEvents.V2 (10.7+)
* /Library/Preferences/SystemConfiguration/preferences.plist (e.g. NETBIOS name, USB interfaces, DNS servers)
* /Library/Preferences/SystemConfiguration/com.apple.smb.server.plist (NETBIOS name)
* /Library/Preferences/.GlobalPreferences.plist (timezone)
* ~/.Trash (trash folder for user)
* ~/.Trash/.DS_Store (trash log. Useful to know the original path of deleted files. Use hexdump -C and then look for ptbLustr. Before is the name of the deleted file, after is the directory where it was located.) 
* /System/Library/CoreServices/SystemVersion.plist
* /System/Library/CoreServices/ServerVersion.plist (if server)
* /.fseventsd (events generated by file system. Used by applications to receive notification on FS changes. Can be parsed using FSEventsParser tool)
* /.MobileBackups and /Volumes/MobileBackups/ (TimeMachine backups)
* /.Spotlight‐V100 (spotlight metadata)
* /.DocumentRevisions‐V100 (contains revisions of documents)
* .DS_Store files in general can be used to look for deleted files on directories.

## System logs
* /Library/Logs
* /private/var/log (multiple logs. system.log caputes clock changes, mounted volumes, user authentication, commands executed via sudo). system.log appears on 10.8 and merges kernel.log, secure.log and system.log.
Also, starting on 10.4, Apple System Log (ASL) is introduced and contains more information than system.log.
  * /private/var/log/asl.log (10.4)
  * /private/var/log/asl.db (10.5 – 10.5.6)
  * /private/var/log/*.asl (10.5.6 - 10.12)
* /private/var/log/daily.out (e.g. interface statistics, disk status, up time)
  
Starting on 10.12, the unified logging was created. Unified logging files are stored on:
* /private/var/db.
* /private/var/db/diagnostics/
* /private/var/db/uuidtext

## Audit Logs (>10.3)
* /private/var/audit (e.g. file system activity, process creation, user activity)
* /var/audit


## User-Specific Logs
* ~/Libraray/Logs

## Application-Specific Logs
* /Applications/<Bundle>
* /Library/Logs
* /Library/Application Support/<Application>


## Commands
* system_profiler –xml –detaillevel full (reports hardware and software information)
* ls -la /etc/localtime (timezone)
* plutil -p [PLIST_FILE] (shows plist file in human readable form)
* lsbom [BOM_FILE] (opens BOM file)
* syslog -T [TIME_ZONE] -F [FORMAT] -f [FILE_PATH] (read ASL file)
* log show [FILE_PATH] (shows inified log file)
* praudit -xn [FILE_PATH] (show audit log file in XML format)
* xattr –p [ATTRIBUTE_NAME] [FILE_NAME] (query extended attributes for file). ls -la can be used to check whether a file has extended attributes (look for a @ on the permissions).
* mdls -name [ATTRIBUTE_NAME] [FILE] (queries spotlight metadata attribute for file). kMDItemWhereFroms can be used to check the source of the download.
* ioreg -p IODeviceTree -n chosen (useful to inspect boot UUID to interpret some log entries. )
* stat -x [FILE] (e.g. inode, timestamps)
* kexstat (check loaded extensions)
* sysctl (query Kernel information)
* uname -a (queries kernel information)
