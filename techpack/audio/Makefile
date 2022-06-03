# Use USERINCLUDE when you must reference the UAPI directories only.
USERINCLUDE     += \
                -I$(srctree)/techpack/audio/include/uapi \
                -I$(srctree)/techpack/audio/include

# Use LINUXINCLUDE when you must reference the include/ directory.
# Needed to be compatible with the O= option
LINUXINCLUDE    += \
                -I$(srctree)/techpack/audio/include/uapi \
                -I$(srctree)/techpack/audio/include

obj-$(CONFIG_SND_SOC_TFA9874)	+= asoc/codecs/tfa9874/

obj-y += soc/
obj-y += dsp/
obj-y += ipc/
obj-y += asoc/
