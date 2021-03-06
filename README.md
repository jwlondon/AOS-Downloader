#Apple Open Source Downloader

This script allows for query and fetching of various open source releases from opensource.apple.com.

To build off this script, use the AOSD.py file as a library.

##Usage:

	$ python fetch.py [-h] -t TYPE [-l] [-v VERSION] [-p PACKAGE] [-b BUILD] [-d DIFF]

* TYPE
  * mac - Query OS X releases
  * ios - Query iOS releases
  * dev - Query Developer Tool releases
  * server - Query OS X Server releases

* VERSION 
  * the release version to query a package list of

* PACKAGE
  * the name of the package to query

* BUILD
  * the build number of the package to download

* DIFF
  * the version to take a diff to

##Examples:

###Fetch package list for 10.9.5
	$ python fetch.py -t mac -v 10.9.5 -l
	Getting OS X Packages...
	Found version!
	Downloading packages list...
	Package: AppleFileSystemDriver - 17
	Package: AppleRAID - 4.0.6
	Package: AppleUSBCDCDriver - 4201.2.5
	Package: AppleUSBIrDA - 145.2.4
	Package: AvailabilityVersions - 6
	Package: BerkeleyDB - 21
	Package: BootCache - 106
	Package: CF - 855.17
	Package: CPAN - 52
	...

###Fetch release of 'vim'
	$ python fetch.py -t mac -p vim -l
	Getting OS X Packages...
	No build number specified, searching all versions of OS X for builds of "vim". This may take a few minutes...
	10 - 10.3
	34 - 10.5
	13 - 10.4
	47 - 10.7
	43 - 10.6
	53 - 10.9
	48.1 - 10.8
	39 - 10.5.8
	44 - 10.6.3


###Fetch tarball of xnu-2422.110.17
	$ python fetch.py -t mac -p xnu -b 2422.110.17
	Getting OS X Packages...
	Downloading "xnu-2422.110.17.tar.gz"...
	Download Complete!


###Create Diff of CF 744 to 855.11
	$  python fetch.py -t mac -p CF -b 744 -d 855.11
	Getting OS X Packages...
	Downloading "CF-744.tar.gz"...
	Download Complete!
	Decompressing CF-744.tar.gz -> CF-744
	Decompression Complete!
	Downloading "CF-855.11.tar.gz"...
	Download Complete!
	Decompressing CF-855.11.tar.gz -> CF-855.11
	Decompression Complete!
	Creating source diff...


###Fetch all of 10.8.3

	$ python fetchall.py -t mac -v 10.8.3


