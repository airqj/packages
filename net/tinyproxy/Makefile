#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tinyproxy
PKG_VERSION:=1.11.1
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://github.com/tinyproxy/tinyproxy/releases/download/$(PKG_VERSION)
PKG_HASH:=d66388448215d0aeb90d0afdd58ed00386fb81abc23ebac9d80e194fceb40f7c

PKG_MAINTAINER:=Jo-Philipp Wich <jo@mein.io>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:tinyproxy_project:tinyproxy

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

TARGET_LDFLAGS += -static

include $(INCLUDE_DIR)/package.mk

define Package/tinyproxy
  SUBMENU:=Web Servers/Proxies
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Tinyproxy is a lightweight HTTP and HTTPS proxy
  URL:=https://tinyproxy.github.io/
endef

define Package/tinyproxy/conffiles
/etc/config/tinyproxy
endef

CONFIGURE_VARS += ac_cv_path_A2X=no

define Package/tinyproxy/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/tinyproxy $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/share/tinyproxy
	$(CP) $(PKG_INSTALL_DIR)/usr/share/tinyproxy/*.html $(1)/usr/share/tinyproxy/
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/tinyproxy.config $(1)/etc/config/tinyproxy
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/tinyproxy.init $(1)/etc/init.d/tinyproxy
endef

$(eval $(call BuildPackage,tinyproxy))
