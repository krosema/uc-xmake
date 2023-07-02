# Makefile for cross-compilation
# STM32F1

.PHONY:

SDK=		~/uc/a32/stm32f1/STM32F10x_StdPeriph_Lib_V3.6.0
SYS_DEV_H=	system_stm32f10x.h
SYS_DEV_C=	system_stm32f10x.c
STARTUP_S=	startup_stm32f10x_md_vl.s
LINKER_LD=	stm32_flash.ld
LIBCONF_H=	stm32f10x_conf.h
STARTUP_O=	$(STARTUP_S:.s=.o)
SYS_DEV_O=	$(SYS_DEV_C:.c=.o)
makefile?=	makefile.proj

links:
	# top-level directory
	mkdir $(dir)

	# directory for .o's
	mkdir $(dir)/obj

	# architecture
	ln -s $(SDK)/Libraries/CMSIS/CM3/CoreSupport/ $(dir)/cmsis

	# device
	ln -s $(SDK)/Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/ $(dir)/device

	# setup files
	ln -s $(SDK)/Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/$(SYS_DEV_H) $(dir)/$(SYS_DEV_H)
	ln -s $(SDK)/Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/$(SYS_DEV_C) $(dir)/$(SYS_DEV_C)
	ln -s $(SDK)/Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/startup/gcc_ride7/$(STARTUP_S) $(dir)/$(STARTUP_S)

	# linker script
	ln -s $(SDK)/Project/STM32F10x_StdPeriph_Template/TrueSTUDIO/STM32100B-EVAL/$(LINKER_LD) $(dir)/$(LINKER_LD)

	# libs
	ln -s $(SDK)/Libraries/STM32F10x_StdPeriph_Driver/inc $(dir)/inc
	ln -s $(SDK)/Libraries/STM32F10x_StdPeriph_Driver/src $(dir)/src
	cp $(SDK)/Project/STM32F10x_StdPeriph_Template/$(LIBCONF_H) $(dir)/$(LIBCONF_H)

	# local makefile

	echo '# Bootstrap requirements' >> $(dir)/makefile
	echo 'OBJS+=\tobj/$(STARTUP_O)' >> $(dir)/makefile
	echo 'OBJS+=\tobj/$(SYS_DEV_O)' >> $(dir)/makefile
	echo '' >> $(dir)/makefile
	echo 'LINKER_LD=\t$(LINKER_LD)' >> $(dir)/makefile
	echo '' >> $(dir)/makefile
	cat $(makefile) >> $(dir)/makefile
