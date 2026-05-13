obj-$(CONFIG_SENSORS_HALL)		+= hall_sensor.o

KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build
M ?= $(shell pwd)

KBUILD_OPTIONS += CONFIG_SENSORS_HALL=m

-include $(KERNEL_SRC)/../../../../private/google-modules/Makefile.include

modules modules_install clean compile_commands.json:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $(KBUILD_OPTIONS) $(@)
