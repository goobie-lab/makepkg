# makepkg
A set of tools and scripts for building and checking Debian/RedHat packages from Makefiles.

<h1>Writing a Makefile</h1>
Typical Makefile pattern:
```
# Specify the package base name in variable PKGNAME,
# without version id nor architecture suffix.
PKGNAME := <MyPackage>

# Uncomment the 2 follolwing lines if the package is architecture-independent,
# i.e. if it does not contain natively executable code.
# Default value is the architecture of the current machine.
#DEBARCH := all
#RPMARCH := noarch

all:
	<Put your build rules here>

# Include makepkg rules
include /usr/share/makepkg/pkg.mk

# Copy the files to be packaged in the staging directory $(DESTDIR)
# By default, DESTDIR = out/root
install:
	mkdir -p $(DESTDIR)/...
	<Copy files to $(DESTDIR)>
```

<h1>Generate a.deb or .rpm package</h1>
Generate a Debian package:
```
$ make deb
```
Generate a RedHat package:
```
$ make rpm
```
