M ?= $(shell pwd)

KBASE_PATH_RELATIVE = $(M)


-include $(KERNEL_SRC)/../../../../private/google-modules/Makefile.include

modules modules_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) CONFIG_TRUSTY=m CONFIG_TRUSTY_VIRTIO_IPC=m \
	EXTRA_CFLAGS="$(EXTRA_CFLAGS)" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)
