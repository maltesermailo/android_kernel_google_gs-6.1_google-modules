# SPDX-License-Identifier: GPL-2.0-only

subdir-ccflags-y += \
		-I$(KERNEL_SRC)/../../../../private/google-modules/bms

obj-$(CONFIG_GOOGLE_BCL) += google_bcl.o
google_bcl-y			+= google_bcl_core.o
google_bcl-y			+= google_bcl_irq_mon.o
google_bcl-y			+= google_bcl_sysfs.o
google_bcl-y			+= google_bcl_util.o
google_bcl-y			+= google_bcl_qos.o
google_bcl-y			+= google_bcl_debugfs.o
google_bcl-y			+= max77759_vdroop.o
google_bcl-y			+= max77779_vdroop.o
google_bcl-y			+= google_bcl_data_logging.o
# ifeq ($(filter y, $(CONFIG_REGULATOR_S2MPG10)),)
ifneq ($(filter m,$(CONFIG_REGULATOR_S2MPG12)$(CONFIG_REGULATOR_S2MPG14)),)
	google_bcl-y			+= google_bcl_votable.o
endif

KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build
M ?= $(shell pwd)

EXTRA_SYMBOLS += $(OUT_DIR)/../../../../private/google-modules/bms/Module.symvers
EXTRA_SYMBOLS += $(OUT_DIR)/../../../../private/google-modules/bms/misc/Module.symvers

ifneq ($(wildcard $(OUT_DIR)/../../../../private/google-modules/radio/samsung/*/Module.symvers),)
EXTRA_SYMBOLS += $(OUT_DIR)/../../../../private/google-modules/radio/samsung/*/Module.symvers
endif

KBUILD_OPTIONS += CONFIG_GOOGLE_BCL=m
KBUILD_OPTIONS += CONFIG_REGULATOR_S2MPG12=m CONFIG_EXYNOS_PM_QOS=y
EXTRA_CFLAGS += -DCONFIG_SOC_GS201=1 -DCONFIG_SOC_GOOGLE=1 -DCONFIG_REGULATOR_S2MPG12=1 -DCONFIG_DRV_SAMSUNG_PMIC=1 -DCONFIG_GOOGLE_MODEMCTL=1 -DCONFIG_EXYNOS_PM_QOS=1 -DCONFIG_PINCTRL_EXYNOS_GS=1
include $(KERNEL_SRC)/../../../../private/google-modules/soc/gs/Makefile.include

modules modules_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) \
	$(KBUILD_OPTIONS) EXTRA_CFLAGS="$(EXTRA_CFLAGS)" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)
