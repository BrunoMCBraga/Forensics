
# OSX Artifacts

Some artifacts may not be present on all OSX versions.

## Installs And Updates
* /Library/Preferences/com.apple.SoftwareUpdate.plist (updates)
* /Library/Receipts/InstallHistory.plist and /private/var/log/install.log (software installatiom history)
* /var/db/receipts/, /private/var/db/recipts/ (BOM files)
* /Applications/[Application].app/Contents/_MASReceipt/receipt (BOM files for application)
* /private/var/log/install.log (only applications installed through packages)

## Network
* /private/var/db/dhcpclient/leases/ (dhcp leases)
* /etc/hosts (mapping hostname, IP)

## Wireless
* /Library/Preferences/SystemConfiguration/com.apple.airport.preferences.plist
* /Library/Preferences/SystemConfiguration/com.apple.network.identification.plist (OSX <10.9) 

## Misc
* /Library/Preferences/SystemConfiguration/preferences.plist (e.g. NETBIOS name, USB interfaces, DNS servers)
* /Library/Preferences/SystemConfiguration/com.apple.smb.server.plist (NETBIOS name)
* /Library/Preferences/.GlobalPreferences.plist (timezone)
* ~/.Trash (trash folder for user)
* ~/.Trash/.DS_Store (trash log. Useful to know the original path of deleted files. Use hexdump -C and then look for ptbLustr. Before is the name of the deleted file, after is the directory where it was located.)

## GUI
* ~/Library/Preferences/com.apple.finder.plist (e.g. volumes and recent files)
* ~/Library/Preferences/com.apple.sidebarlists.plist
* ~/Library/Application Support/com.apple.sharedfilelist/com.appleLSSharedFileList.FavoriteServers.sfl
* ~/Library/Preferences/com.apple.dock.plist
* ~/Library/Preferences/com.apple.desktop.plist 
* ~/Library/Application Support/Dock/desktoppicture.db
* ~/Library/Preferences/com.apple.spaces.plist
* ~/Library/Saved Application State/<Bundle ID>.savedState ~/Library/Containers/<BundleID>/Data/Library/Saved Application State/

## Recent folders, executed applications and volumes
* ~/Library/Preferences/com.apple.finder.plist
* ~/Library/Preferences/com.apple.DiskUtility.plist
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

## Accounts
* /Library/Preferences/com.apple.preferences.accounts.plist (deleter users)
* /Library/Preferences/com.apple.loginwindow.plist (e.g. last connected user, whether there is a autologin user, password for autologin)
* /private/var/db/dslocal/nodes/Default/users/[username].plist and /private/var/db/dslocal/nodes/Default/groups/[groupname].plist (information about users and groups)
* ~/Library/Accounts/Accounts3.sqlite (e.g. Mail.app, Messages, Social Media)

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

### Shell History
* ~/.sh_history (Korn shell)
* ~/.bash_history (Bash)
* ~/.zsh_history/, ~/.zhistory, ~./history (Zshell. If none of those work, check ~/.zshrc for the location of the file).
* ~/.bash_sessions/<GUID>.history (>10.11)
* /var/root/[ONE_OF_THE_ABOVE]

## Backups
* /Library/Preferences/com.apple.TimeMachine.plist
* /var/db/com.apple.TimeMachine.SnapshotDates.plist

## Volumes, File System and Boot information
* /System/Library/CoreServices/boot.efi (boot UUID)
* ~/Library/Logs/DiskUtility.log
* ~/Library/Logs/fsck_hfs.log or ~/Library/Logs/fsck_apfs.log (HFS and APFS file system check log)


## Printing
* /var/log/cups/page_log
* /var/log/cups/access_log
* /private/var/spool/cups (printing jobs. Can be parsed using cups_control from http://jafat.sourceforge.net/)
* /etc/cups/printers.conf + /Library/Preferences/org.cups.printers.plist: printer information
* /private/var/log/cups/access_log 
* /private/var/log/cups/error_log 
* /private/var/log/cups/page_log 


## Misc
* ~/Downloads (user downloads)
* ~/.ssh/known_hosts (hostnames, IPs and keys for SSH sessions)
* ~/Library/Application Support/Screen Sharing/*.vncloc (<10.10)
* ~/Library/Containers/com.apple.ScreenSharing/Data/Library/Application Support/Screen Sharing/*.vncloc (>10.11)
* File Quarantine (for files downloaded from the internet):
 * /Library/Containers/<bundle_id>/Data/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV2 (10.11)
 * ~/Library/Preferences/com.apple.LaunchServices.QuarantineEvents
 * ~/Library/Preferences/com.apple.LaunchServices.QuarantineEvents.V2 (10.7+)

## System logs
* /Library/Logs
* /private/var/log (multiple logs. system.log caputes clock changes, mounted volumes, user authentication, commands executed via sudo). system.log appears on 10.8 and merges kernel.log, secure.log and system.log.
Also, starting on 10.4, Apple System Log (ASL) is introduced and contains more information than system.log.
  * /private/var/log/asl.log (10.4)
  * /private/var/log/asl.db (10.5 – 10.5.6)
  * /private/var/log/*.asl (10.5.6 - 10.12)
  
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

## Daily Log
* /private/var/log/daily.out (e.g. interface statistics, disk status, up time)


Commands:
* system_profiler –xml –detaillevel full (reports hardware and software information)
* ls -la /etc/localtime (timezone)
* plutil -p [PLIST_FILE] (shows plist file in human readable form)
* lsbom [BOM_FILE] (opens BOM file)
* syslog -T [TIME_ZONE] -F [FORMAT] -f [FILE_PATH] (read ASL file)
* log show [FILE_PATH] (shows inified log file)
* praudit -xn [FILE_PATH] (show audit log file in XML format)
* xattr –p [ATTRIBUTE_NAME] [FILE_NAME] (query extended attributes for file). ls -la can be used to check whether a file has extended attributes (look for a @ on the permissions).
* mdls -name [ATTRIBUTE_NAME] [FILE] (queries spotlight metadata attribute for file). kMDItemWhereFroms can be used to check the source of the download.

#######################################################################################################################################
Also, kernel.log can be used to search for network country code.
Kernel.log:
* Mac addresses

Daily.log:
* Disk Usage History
* Time Zone Changes


What is on system.log:
* Backup logs
* Boot/reboot/shutdown
