# SPDX-License-Identifier: GPL-2.0
#
# Makefile for Google Battery Management System
#

KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build
M ?= $(shell pwd)

EXTRA_CFLAGS += -DDYNAMIC_DEBUG_MODULE
KBUILD_OPTIONS += CONFIG_GOOGLE_VOTABLE=m CONFIG_GOOGLE_LOGBUFFER=m

modules modules_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) \
	CONFIG_GOOGLE_VOTABLE=m CONFIG_GOOGLE_LOGBUFFER=m EXTRA_CFLAGS="$(EXTRA_CFLAGS)" $(@)

print-%:
	@echo $* = $($*)

value-%:
	@echo $($*)
