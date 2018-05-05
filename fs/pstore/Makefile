#
# Makefile for the linux pstorefs routines.
#

# Huaqin add for ZQL1650-358 by liunianliang at 2018/02/08 start
ccflags-y    := -DDEBUG
# Huaqin add for ZQL1650-358 by liunianliang at 2018/02/08 end

obj-$(CONFIG_PSTORE) += pstore.o

pstore-objs += inode.o platform.o
pstore-$(CONFIG_PSTORE_FTRACE)	+= ftrace.o

pstore-$(CONFIG_PSTORE_PMSG)	+= pmsg.o

ramoops-objs += ram.o ram_core.o
obj-$(CONFIG_PSTORE_RAM)	+= ramoops.o
