#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=aircrack-ng
PKG_VERSION:=1.2-rc2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://download.aircrack-ng.org/ \
	http://archive.aircrack-ng.org/aircrack-ng/$(PKG_VERSION)/
#PKG_MD5SUM:=c2f8648c92f7e46051c86c618d4fb0d5
PKG_MD5SUM:=ebe9d537f06f4d6956213af09c4476da

PKG_BUILD_PARALLEL:=0
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/aircrack-ng
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpthread +libopenssl +libpcap +libnl-tiny
  TITLE:=next generation of aircrack with new features
  URL:=http://www.aircrack-ng.org/
  SUBMENU:=wireless
endef

define Package/aircrack-ng/description
Aircrack-ng is the next generation of aircrack with new features
endef

MAKE_FLAGS += \
	CFLAGS="$(TARGET_CFLAGS) -Wall -Iinclude/ $(TARGET_CPPFLAGS) -D_REVISION=0" \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	OSNAME=Linux \
	prefix="/usr" \
	sqlite="false" \

define Package/aircrack-ng/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,aircrack-ng))
