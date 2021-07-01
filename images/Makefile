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

BINLILO := ../src/lilo
BMPS8 := coffee.bmp
BMPS4 := debian.bmp debian-de.bmp debianlilo.bmp inside.bmp onlyblue.bmp tuxlogo.bmp
NAME8 := coffee
NAME4 := debian debian-de debianlilo inside onlyblue tuxlogo


all: $(BMPS4) $(BMPS8)

$(BMPS4): %.bmp: %_16c.uu
	uudecode $<
	@echo Y | $(BINLILO) -E $(addsuffix .dat,$(basename $<)) 1>/dev/null

$(BMPS8): %.bmp: %_256c.uu
	uudecode $<
	@echo Y | $(BINLILO) -E $(addsuffix .dat,$(basename $<)) 1>/dev/null

install: all
	mkdir -p $$DESTDIR$(BOOT_DIR)
	install -m 0644  $(BMPS4) $(BMPS8)  $$DESTDIR$(BOOT_DIR)
	for i in $(NAME8); do \
		cp $${i}_256c.dat $$DESTDIR$(BOOT_DIR)/$${i}.dat; \
	done
	for i in $(NAME4); do \
		cp $${i}_16c.dat $$DESTDIR$(BOOT_DIR)/$${i}.dat; \
	done

clean:
	rm -f $(BMPS4) $(BMPS8)

distclean: clean

uninstall:
	(cd $$DESTDIR$(BOOT_DIR); rm -f $(BMPS4) $(BMPS8))
	for i in $(NAME4) $(NAME8); do \
		rm -f $$DESTDIR$(BOOT_DIR)/$${i}.dat; \
	done

