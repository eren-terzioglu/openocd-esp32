# Makefile to compile the flasher stub program
#
# Note that YOU DO NOT NEED TO COMPILE THIS IN ORDER TO JUST USE

# See the comments in the top of the Makefile for parameters that
# you probably want to override.
#
# Copyright (c) 2017 Espressif Systems
# All rights reserved
#
#
# This program is free software; you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation; either version 2 of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with
# this program; if not, write to the Free Software Foundation, Inc., 51 Franklin
# Street, Fifth Floor, Boston, MA 02110-1301 USA.

# Prefix for ESP32-S2 cross compilers (can include a directory path)
CROSS ?= xtensa-esp32s2-elf-

# Path to the esp-idf root dir
IDF_PATH ?= ../..

STUB_CHIP_PATH := $(shell pwd)
STUB_COMMON_PATH := $(STUB_CHIP_PATH)/..
STUB_CHIP_ARCH_PATH := $(STUB_COMMON_PATH)/xtensa
STUB_OBJ_DEPS := sdkconfig.h
STUB_LD_SCRIPT := stub.ld
STUB_CHIP := ESP32S2

SRCS := $(IDF_PATH)/components/app_trace/port/xtensa/port.c \
	$(IDF_PATH)/components/xtensa/eri.c \
	$(IDF_PATH)/components/esp_hw_support/port/esp32s2/rtc_clk.c \
	$(IDF_PATH)/components/esp_hw_support/port/esp32s2/rtc_clk_init.c \
	$(IDF_PATH)/components/esp_hw_support/port/esp32s2/rtc_time.c \
	$(IDF_PATH)/components/esp_hw_support/port/esp32s2/regi2c_ctrl.c

CFLAGS := -mlongcalls -mtext-section-literals

INCLUDES := -I$(IDF_PATH)/components/esp32s2/include -I$(IDF_PATH)/components/soc/esp32s2/include \
	-I$(IDF_PATH)/components/esp_rom/include/esp32s2 -I$(IDF_PATH)/components/xtensa/esp32s2/include \
	-I$(IDF_PATH)/components/hal/esp32s2/include \
	-I$(IDF_PATH)/components/esp_hw_support/port/esp32s2/private_include \
	-I$(IDF_PATH)/components/esp_hw_support/port/esp32s2 \
	-I$(IDF_PATH)/components/xtensa/include \
	-I$(IDF_PATH)/components/freertos/include \
	-I$(IDF_PATH)/components/freertos/port/xtensa/include

DEFINES :=

LDFLAGS := -L$(IDF_PATH)/components/esp32s2/ld -T$(IDF_PATH)/components/esp_rom/esp32s2/ld/esp32s2.rom.ld \
	-T$(IDF_PATH)/components/esp_rom/esp32s2/ld/esp32s2.rom.newlib-funcs.ld \
	-T$(IDF_PATH)/components/esp_rom/esp32s2/ld/esp32s2.rom.spiflash.ld -T$(IDF_PATH)/components/esp_rom/esp32s2/ld/esp32s2.rom.api.ld \
	-T$(IDF_PATH)/components/esp_rom/esp32s2/ld/esp32s2.rom.libgcc.ld

include ../stub_common.mk