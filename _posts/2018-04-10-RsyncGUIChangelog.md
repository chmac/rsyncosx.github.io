---
layout: post
title:  "RsyncGUI Changelog"
permalink: RsyncGUIChangelog
---
RsyncGUI is compiled with support for macOS El Capitan version 10.11 - macOS Mojave version 10.14. The application is implemented in Swift 4 by using Xcode 10.

Rsync is a file-based synchronization and backup tool. There is no custom solution for the backup archive. You can quit utilizing RsyncGUI (and rsync) at any time and still have access to all synchronized files.

The [App Sandboxing technology](https://developer.apple.com/app-sandboxing/) is a technology for protecting the user for malicious software. To release a macOS app on Apple Mac App Store require the app to execute inside a sandbox. RsyncGUI is an adapted version of [RsyncOSX](https://github.com/rsyncOSX/RsyncOSX) to execute inside a sandbox. There are a few limitations compared to RsyncOSX. Due to limitations within the Sandbox technology executing third party command line utilities is not allowed.

## Limitations

The default version of `rsync` in macOS is old (version 2.6.9, [protocol](https://rsync.samba.org/how-rsync-works.html) version 29). Version [2.6.9](https://download.samba.org/pub/rsync/src/rsync-2.6.9-NEWS) was released in nov 2006. The current release of rsync is version [3.1.3](https://download.samba.org/pub/rsync/src/rsync-3.1.3-NEWS) protocol 31 released 28 January 2018.

Utilizing **snapshots** in RsyncGUI is for the moment **not possible** due to bugs in default version of rsync version 2.6.9. It is not allowed due to the sandbox to execute an updated version of rsync in e.g `/usr/local/bin`.

Utilizing **scheduled** task is not implemented in RsyncGUI.

If you need either of them please use [RsyncOSX](https://github.com/rsyncOSX/RsyncOSX).

## Version 1.0.1

Version 1.0.1 is released 4 February 2019. Some minor bugfixes after initial release.

## Version 1.0.0

The app is [released](https://itunes.apple.com/us/app/rsyncgui/id1449707783?l=nb&ls=1&mt=12) on Apple Mac App Store 24 January 2019.
