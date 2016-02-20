
Packages
--------

### ffmpeg

* We package the latest stable release. I usually package new versions in externals-dev as they come out.
* ffmpeg doesn't usually break CLI compatibility between releases.
* However, it does sometimes make major changes to codec support in major versions. For example, ffmpeg 3.0 removed support for two AAC encoders, which required some changes in our packaging.
* ffmpeg's libraries, like libavcodec, are built as separate packages in the Debian build process. The packages include the library versions' names in them; this allows several versions to be installed side-by-side. When upgrading, [check the library versions](http://ffmpeg.org/download.html) and update the library names in the debian/control file and other files in the debian directory if necessary.

### Siegfried

* The debian directory for Siegfried comes in the upstream tarball. However, the Debian changelog is maintained locally by us, since it's distro-specific.
* Siegfried is written in Go and needs the Go compiler.
* 1.4.5 and newer include vendored Go dependencies, so you don't have to worry about fetching/installing them separately. You need at least Go 1.5 (with the GO15VENDOREXPERIMENT environment variable set to 1), or Go 1.6 to install with the vendored dependencies.
* We used to package Siegfried's dependencies separately, before they were vendored. Those packages can probably be safely deleted now.

### bulk_extractor

Our packaging files are backported from the ones used in newer versions of Debian/Ubuntu.

### sleuthkit

Our packaging files are backported from the ones used in newer versions of Debian/Ubuntu.

We also backported two of its dependencies, libbfio and libewf, from trusty to precise.

### exiftool

We track production releases from [the official website](http://owl.phy.queensu.ca/~phil/exiftool/history.html). Our packaging files were originally based on Debian's.

### bagit

We maintain these packages ourselves.

### fits

We maintain these packages ourselves. We stopped tracking new releases awhile ago; might be worth updating, but we'd have to make sure nothing has broken our packaging or our workflows.

### nailgun and nailgun-client

We backported these from a recent version of Debian in order to use with fits.

### fido

We maintain this package ourselves.

The upcoming version of Fido introduces a new Python dependency, python-olefile. I have packages for 14.04+ but it's not compatible with 12.04, so it may need to be reworked.

### tika

We added this for experimental purposes but never followed up with it.

### unar

Backported from newer Ubuntu so we could apply a [critical patch](https://bitbucket.org/WAHa_06x36/theunarchiver/issues/753/lsar-json-output-is-incorrect-for-double) that's needed for our usecases. The next release will probably be fine for us, but I don't know how long that will take to filter into the distros we use.

### dh_virtualenv

This is a buildtool that we use to package the Storage Service. It was first introduced to Ubuntu after 14.04, so we backported it to 12.04 and 14.04.

### dh_golang

This is a Go debhelper buildtool. It's in 14.04, but we backported it from that version to 12.04.

### go

Siegfried needs quite modern versions of Go, so we backported 1.4, 1.5, and 1.6 to all the versions of Ubuntu we package for.
