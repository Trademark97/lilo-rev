# -*- makefile -*-
#
# Copyright 2011-2014 Joachim Wiedorn
# All rights reserved.
#
# Licensed under the terms contained in the file 'COPYING'
# in the source directory.
#

# adding variables
include ../make.vars

# install also chattr-lilo hooks
CHATTR := n

POSTUPD  := initramfs/post-update.d
POSTINST := kernel/postinst.d
POSTRM   := kernel/postrm.d
PREINST  := kernel/preinst.d
PRERM    := kernel/prerm.d

all:

install:
	mkdir -p $$DESTDIR$(CFG_DIR)/$(POSTUPD)
	mkdir -p $$DESTDIR$(CFG_DIR)/$(POSTINST)
	mkdir -p $$DESTDIR$(CFG_DIR)/$(POSTRM)
	install -m 0755  $(POSTUPD)/runlilo  $$DESTDIR$(CFG_DIR)/$(POSTUPD)
	install -m 0755  $(POSTINST)/zz-runlilo  $$DESTDIR$(CFG_DIR)/$(POSTINST)
	install -m 0755  $(POSTRM)/zz-runlilo  $$DESTDIR$(CFG_DIR)/$(POSTRM)
  ifeq "$(CHATTR)" "y"
	mkdir -p $$DESTDIR$(CFG_DIR)/$(PREINST)
	mkdir -p $$DESTDIR$(CFG_DIR)/$(PRERM)
	install -m 0755 $(POSTINST)/chattr-lilo  $$DESTDIR$(CFG_DIR)/$(POSTINST)
	install -m 0755 $(PREINST)/chattr-lilo  $$DESTDIR$(CFG_DIR)/$(PREINST)
	install -m 0755 $(PRERM)/chattr-lilo  $$DESTDIR$(CFG_DIR)/$(PRERM)
  endif

clean:

distclean:

uninstall:
	rm -f $$DESTDIR$(CFG_DIR)/$(POSTUPD)/runlilo
	rm -f $$DESTDIR$(CFG_DIR)/$(POSTINST)/zz-runlilo
	rm -f $$DESTDIR$(CFG_DIR)/$(POSTRM)/zz-runlilo
  ifeq "$(CHATTR)" "y"
	rm -f $$DESTDIR$(CFG_DIR)/$(POSTINST)/chattr-lilo
	rm -f $$DESTDIR$(CFG_DIR)/$(PREINST)/chattr-lilo
	rm -f $$DESTDIR$(CFG_DIR)/$(PRERM)/chattr-lilo
  endif
