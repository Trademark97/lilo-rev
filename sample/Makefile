# -*- makefile -*-
#
# Copyright 2009-2014 Joachim Wiedorn
# All rights reserved.
# 
# Licensed under the terms contained in the file 'COPYING'
# in the source directory.
#

# adding variables
include ../make.vars

all:

install:
	mkdir -p $$DESTDIR$(CFG_DIR)
	install -m 0644 lilo.example.conf $$DESTDIR$(CFG_DIR)/lilo.conf_example

clean:

distclean:

uninstall:
	rm -f $$DESTDIR$(CFG_DIR)/lilo.conf_example
