M ?= $(shell pwd)
O ?= $(OUT_DIR)
OBJTREE ?= $(O)/$(M)

KBASE_PATH_RELATIVE = $(M)

EXTRA_CFLAGS += -DDYNAMIC_DEBUG_MODULE=1

EXTRA_CFLAGS += -Werror
EXTRA_CFLAGS += -DCONFIG_SOC_GS201=1 -DCONFIG_DRM_SAMSUNG_DECON=1 -DCONFIG_EXTCON=1 -DCONFIG_DRM_SAMSUNG_DPP=1 -DCONFIG_DRM_SAMSUNG_DSI=1
EXTRA_CFLAGS += -I$(KERNEL_SRC)/drivers/usb/dwc3
EXTRA_CFLAGS += -DCONFIG_SOC_GS201=1 -DCONFIG_DRM_SAMSUNG_DECON=1 -DCONFIG_EXTCON=1 -DCONFIG_DRM_SAMSUNG_DPP=1 -DCONFIG_DRM_SAMSUNG_DSI=1
EXTRA_CFLAGS += -I$(KERNEL_SRC)/drivers/usb/dwc3

include $(KERNEL_SRC)/../../../../private/google-modules/soc/gs/Makefile.include

EXTRA_SYMBOLS  += $(OUT_DIR)/../../../../private/google-modules/bms/misc/Module.symvers
EXTRA_SYMBOLS  += $(OUT_DIR)/../../../../private/google-modules/hdcp/samsung/Module.symvers
EXTRA_SYMBOLS += $(OUT_DIR)/../../../../private/google-modules/display/common/gs_drm/Module.symvers

-include $(KERNEL_SRC)/../../../../private/google-modules/Makefile.include

modules modules_install headers_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) CONFIG_DRM_SAMSUNG=m CONFIG_DRM_SAMSUNG_DP=m CONFIG_DRM_SAMSUNG_DECON=m CONFIG_DRM_SAMSUNG_DPP=m CONFIG_DRM_SAMSUNG_DSI=m CONFIG_DRM_SAMSUNG_DP_AUDIO=y CONFIG_DRM_PANEL_SAMSUNG_COMMON=m CONFIG_DRM_PANEL_GOOGLE_COMMON=m CONFIG_SOC_GS201=y CONFIG_SOC_GS201=y \
	$(KBUILD_OPTIONS) EXTRA_CFLAGS="$(EXTRA_CFLAGS)" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)

modules_install: headers_install
