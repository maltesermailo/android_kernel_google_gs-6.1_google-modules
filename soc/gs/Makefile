# SPDX-License-Identifier: GPL-2.0

KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build
M ?= $(shell pwd)
O ?= $(OUT_DIR)
OBJTREE ?= $(O)/$(M)

EXTRA_SYMBOLS += $(OUT_DIR)/../../../../private/google-modules/bms/misc/Module.symvers
EXTRA_SYMBOLS += $(OUT_DIR)/../../../../private/google-modules/trusty/Module.symvers

modules modules_install headers_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) \
	CONFIG_TYPEC_MAX77759=m CONFIG_USB_PSY=m CONFIG_GOOGLE_TCPCI_SHIM=m CONFIG_TYPEC_MAX77759_CONTAMINANT=m CONFIG_TYPEC_MAX77779_CONTAMINANT=m CONFIG_MFD_S2MPG12=m CONFIG_MFD_S2MPG13=m CONFIG_SOC_GOOGLE=y CONFIG_SOC_GS201=y CONFIG_SOC_GS=y CONFIG_VH_SYSTRACE=y CONFIG_VH_SYSTRACE=y CONFIG_DRV_SAMSUNG_PMIC=m CONFIG_EXYNOS_PM_QOS=m CONFIG_VH_KERNEL=y CONFIG_VH_SYSTRACE=m EXTRA_CFLAGS="-Wno-enum-compare -DCONFIG_SOC_GS201=1 -DCONFIG_SOC_GOOGLE=1 -DCONFIG_DRV_SAMSUNG_PMIC=1 -DCONFIG_EXYNOS_PM_QOS=1 -DCONFIG_PINCTRL_EXYNOS_GS=1" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)

modules_install: modules_preinstall headers_install

include $(KERNEL_SRC)/$(M)/Makefile.preinstall
