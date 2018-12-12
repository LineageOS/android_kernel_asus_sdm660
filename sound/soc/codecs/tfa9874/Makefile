# make sure that the environment variables ARCH and CROSS_COMPILE
# are set for your architecture and cross compiler.
# And that KDIR points to the kernel to build against.
#
# e.g.:
# export ARCH=arm
# export CROSS_COMPILE=arm-linux-gnueabihf-
# export KDIR=../linux


# In case of out of tree build, build as a module
# (when build inside kernel we will not enter this directory and this will have no effect)
ifeq ($(CONFIG_SND_SOC_TFA9874),)
CONFIG_SND_SOC_TFA9874 := m
endif

ifneq ($(KERNELRELEASE),)

# debugging support (also enables trace_printk)
EXTRA_CFLAGS += -DDEBUG

EXTRA_CFLAGS += -I$(src)/inc
EXTRA_CFLAGS += -Werror

obj-$(CONFIG_SND_SOC_TFA9874) := snd-soc-tfa9874.o

snd-soc-tfa9874-objs += src/tfa98xx.o
snd-soc-tfa9874-objs += src/tfa_container.o
snd-soc-tfa9874-objs += src/tfa_dsp.o
snd-soc-tfa9874-objs += src/tfa_init.o

ifdef TFA_DEBUG
EXTRA_CFLAGS += -DTFA_DEBUG -DDEBUG
snd-soc-tfa9874-objs += src/tfa_debug.o
endif

ifeq ($(CONFIG_MACH_ASUS_SDM660),y)
EXTRA_CFLAGS += -DTFA9874_NONDSP_STEREO
endif

else

MAKEARCH := $(MAKE) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE)

all:
	$(MAKEARCH) -C $(KDIR) M=$(PWD) modules

clean:
	$(MAKEARCH) -C $(KDIR) M=$(PWD) clean
	rm -f $(snd-soc-tfa98xx-objs)

endif
