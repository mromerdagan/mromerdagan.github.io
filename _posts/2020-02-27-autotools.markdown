---
layout: post
title:  "Autotools"
date:   2020-02-27 10:03:20 +0200
categories: autotools make Makefiles
---

## make targets

Before talking about autotools, it is important to mention the **standart targets** that
are common to most Makefiles out there. These are de-facto standard and should be used
rather than project specific ones, if possible:

	all              Build everyhing
	install          Install artifacts
	install-strip    Install, but strip debug symbols
	clean            Remove Makefile artifacts
	distclean        Same as clean, but also remove autotools artifats
	check            Run test suite
	installcheck     Check installation
	dist             Create source tarball


## fs variables

Another convention that is being used widly in makefiles is filesystem variables. Most
autotools projects would install applications in `/usr/local/bin` by default for example,
but will leave this preference configurable to the user building the package. So, for
example, if one wants to install applications of a package to `/usr/bin` he would have to
change the **prefix** filesystem variable, typically with `configure --prefix=/usr/bin`:


	prefix           Defaults to /usr/local
	exec-prefix      Defaults to prefix
	bindir           Defaults to exec-prefix/bin
	libdir           Defaults to exec-prefix/lib

	includedir       Defaults to prefix/include
	datarootdir      Defaults to prefix/share
	sysconfigdir     Defaults to prefix/etc

All of these are configurable using

	configure --prefix
	configure --sysconfigdir

etc.
