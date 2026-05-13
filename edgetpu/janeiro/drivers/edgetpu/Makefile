# SPDX-License-Identifier: GPL-2.0
#
# Makefile for EdgeTPU framework and dependent drivers.
#

KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build
M ?= $(shell pwd)

KBUILD_OPTIONS += CONFIG_JANEIRO=m

-include $(KERNEL_SRC)/../../../../private/google-modules/soc/gs/Makefile.include
EXTRA_CFLAGS += -I$(KERNEL_SRC)/../../../../private/google-modules/power/mitigation
EXTRA_SYMBOLS	+= $(OUT_DIR)/../../../../private/google-modules/power/mitigation/Module.symvers

-include $(KERNEL_SRC)/../../../../private/google-modules/Makefile.include

modules modules_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $(KBUILD_OPTIONS) \
	EXTRA_CFLAGS="$(EXTRA_CFLAGS)" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)
