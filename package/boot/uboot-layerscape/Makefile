#
# Copyright (C) 2016 Jiang Yutang <jiangyutang1978@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=uboot-layerscape
PKG_VERSION:=v1.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_MIRROR_HASH:=6aba7cb32d655dacb49bd188706bf1284159ae9b1fa69056df634b90070c3768
PKG_SOURCE_URL:=https://github.com/fsl-jyt/u-boot.git
PKG_SOURCE_VERSION:=aefcbf4c2bb36e1f0ead61181e5fe1119b5683ad

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk

define U-Boot/Default
  BUILD_TARGET:=layerscape
  BUILD_SUBTARGET:=64b
  BUILD_DEVICES:=$(1)
  UBOOT_IMAGE:=u-boot-dtb.bin
  HIDDEN:=y
endef

define U-Boot/ls1043ardb
  NAME:=NXP ls1043ardb 64b Dev Board
endef

define U-Boot/ls1046ardb
  NAME:=NXP ls1046ardb 64b Dev Board
  UBOOT_CONFIG:=ls1046ardb_qspi
endef

define U-Boot/ls1012ardb
  NAME:=NXP ls1012ardb 64b Dev Board
  UBOOT_CONFIG:=ls1012ardb_qspi
  UBOOT_IMAGE:=u-boot-swap.bin
endef

UBOOT_TARGETS := \
	ls1043ardb \
	ls1046ardb \
	ls1012ardb

define Build/InstallDev
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/$(UBOOT_IMAGE) $(KERNEL_BUILD_DIR)/$(BUILD_VARIANT)-64b-uboot.bin
endef

define Package/u-boot/install/default
endef

$(eval $(call BuildPackage/U-Boot))
