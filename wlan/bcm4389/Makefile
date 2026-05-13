#
# Copyright (C) 2025, Broadcom.
#
#      Unless you and Broadcom execute a separate written software license
# agreement governing use of this software, this software is licensed to you
# under the terms of the GNU General Public License version 2 (the "GPL"),
# available at http://www.broadcom.com/licenses/GPLv2.php, with the
# following added to such license:
#
#      As a special exception, the copyright holders of this software give you
# permission to link this software with independent modules, and to copy and
# distribute the resulting executable under terms of your choice, provided that
# you also meet, for each linked independent module, the terms and conditions of
# the license of that module.  An independent module is a module which is not
# derived from this software.  The special exception does not apply to any
# modifications of the software.
#
#
# <<Broadcom-WL-IPTag/Open:>>
#
# bcmdhd

# Path to the module source
M ?= $(shell pwd)

ifneq ($(KERNEL_SRC),)
 KBUILD_OPTIONS += BCMDHD_ROOT=$(shell cd $(KERNEL_SRC); readlink -e $(M))
 -include $(KERNEL_SRC)/../../../../private/google-modules/soc/gs/Makefile.include
 EXTRA_CFLAGS+="-Wno-missing-prototypes"
EXTRA_CFLAGS += -DWL_MLO_BKPORT_NEW_PORT_AUTH
EXTRA_CFLAGS += -DCONFIG_SOC_GOOGLE=1 -DCONFIG_SOC_GS201=1 -DCONFIG_PCI=1 -DCONFIG_PCI_EXYNOS_GS=1 -DCONFIG_PCI_EXYNOS_CAL_GS201=1 -DCONFIG_EXYNOS_PM=1 -DCONFIG_EXYNOS_PD_EL3=1
KBUILD_OPTIONS += CONFIG_PCI=y
endif

ifneq ($(KERNEL_SRC),)
 KBUILD_OPTIONS += BCMDHD_ROOT=$(shell cd $(KERNEL_SRC); readlink -e $(M))
endif

# Define and "all" target, which isn't really needed but doesn't hurt.
all: modules

-include $(KERNEL_SRC)/../../../../private/google-modules/Makefile.include

modules modules_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $(KBUILD_OPTIONS) \
		EXTRA_CFLAGS="$(EXTRA_CFLAGS)" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)
