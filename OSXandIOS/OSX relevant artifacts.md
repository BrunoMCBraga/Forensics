
# OSX Artifacts

Some artifacts may not be present on all OSX versions.

## Installs And Updates
* /Library/Preferences/com.apple.SoftwareUpdate.plist (updates)
* /Library/Receipts/InstallHistory.plist and /private/var/log/install.log (software installatiom history)
* /var/db/receipts/ (bill of materials files)
* /Applications/[Application].app/Contents/_MASReceipt/receipt (BOM files for application)
* /private/var/log/install.log

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

## Recent folders and mounted volumes
* ~/Library/Preferences/com.apple.finder.plist
* ~/Library/Preferences/com.apple.DiskUtility.plist
* ~/Library/Preferences/com.apple.sidebarlists.plist (sidebar stuff)


## Accounts
* /Library/Preferences/com.apple.preferences.accounts.plist

## Backups
* /Library/Preferences/com.apple.TimeMachine.plist
* /var/db/com.apple.TimeMachine.SnapshotDates.plist



## Boot UUID
* /System/Library/CoreServices/boot.efi

## Printing
* /var/log/cups/page_log
* /var/log/cups/access_log
* /private/var/spool/cups (printing jobs. Can be parsed using cups_control from http://jafat.sourceforge.net/)
* /etc/cups/printers.conf + /Library/Preferences/org.cups.printers.plist: printer information
* /private/var/log/cups/access_log 
* /private/var/log/cups/error_log 
* /private/var/log/cups/page_log 




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
