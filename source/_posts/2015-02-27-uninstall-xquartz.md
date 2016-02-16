title: The way to uninstall Xquartz
date: 2015-02-27 17:45:58
tags:
  - mac
  - OSX
  - xquartz
  - X11
categories: OSX
---

**Using the following command to uninstall the Xquartz on Mac.**
<br>
``` [shell]
$ launchctl unload /Library/LaunchAgents/org.macosforge.xquartz.startx.plist
$ sudo launchctl unload /Library/LaunchDaemons/org.macosforge.xquartz.privileged_startx.plist
$ sudo rm -rf /opt/X11* /Library/Launch*/org.macosforge.xquartz.* /Applications/Utilities/XQuartz.app /etc/*paths.d/*XQuartz
$ sudo pkgutil --forget org.macosforge.xquartz.pkg
```