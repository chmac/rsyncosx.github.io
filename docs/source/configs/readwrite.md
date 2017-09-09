### Reading and writing data to permanent storage

RsyncOSX holds all data in memory as [Singelton](https://en.wikipedia.org/wiki/Singleton_pattern) objects. When data is loaded from permanent storage all arguments are computed. The object [Readwritefiles.swift](https://github.com/rsyncOSX/RsyncOSX/blob/master/RsyncOSX/Readwritefiles.swift) decides if data should be read from memory or permanent storage. All data (configurations, schedules and log records, user config) is read from permanent storage utilizing the [NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary) foundation class. The singelton class [SharingManagerConfigurations.swift](https://github.com/rsyncOSX/RsyncOSX/blob/master/RsyncOSX/SharingManagerConfiguration.swift) saves the state of data is dirty or not. If not dirty RsyncOSX get the data from memory, if dirty a reread of data is forced before RsyncOSX get data from memory. By this data is only read from permanent storage if there has been a change in data.

RsyncOSX configuration file, scheduled tasks which also includes log records and user configuration are plain XML-files ([property list files](https://en.wikipedia.org/wiki/Property_list)). Files are saved in:

- `~/Documents/Rsync/MacID/configRsync.plist` - configurations
  - `~/` is user home directory
  - `MacID` is the Mac serial number and is automatically set by RsyncOSX
- `~/Documents/Rsync/MacID/scheduleRsync.plist` - scheduled tasks including log records
- `~/Documents/Rsync/MacID/config.plist` - user config

If _profile_ is used:

- `~/Documents/Rsync/MacID/profile/configRsync.plist`
- `~/Documents/Rsync/MacID/profile/scheduleRsync.plist`
  - `profile` is the profile name
- `~/Documents/Rsync/MacID/config.plist` - user config