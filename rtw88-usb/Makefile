#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=rtw88-usb
PKG_VERSION:=1.0.1
PKG_RELEASE:=2
PKG_LICENSE:=GPLv2

PKG_MAINTAINER:=Alexander Rumyankov <alex@rumyankovs.com>
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/rtw88-usb
  SUBMENU:=Wireless Drivers
  TITLE:=rtw88-usb support
  DEPENDS:=+kmod-cfg80211 +kmod-mac80211 +kmod-usb-core +@DRIVER_11N_SUPPORT +@DRIVER_11AC_SUPPORT
  FILES:=\
	$(PKG_BUILD_DIR)/rtw88_pci.ko \
	$(PKG_BUILD_DIR)/rtw88_usb.ko \
	$(PKG_BUILD_DIR)/rtw88_core.ko \
	$(PKG_BUILD_DIR)/rtw88_8821c.ko \
	$(PKG_BUILD_DIR)/rtw88_8821cu.ko
  AUTOLOAD:=$(call AutoProbe, rtw88_8821cu)
  PROVIDES:=kmod-rtw88-usb
endef

define KernelPackage/rtw88-usb/description
 Kernel module for rtw88 usb wireless module.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
                $(KERNEL_MAKE_FLAGS) \
                M="$(PKG_BUILD_DIR)" \
                modules
endef

$(eval $(call KernelPackage,rtw88-usb))
