#
# Copyright (C) 2020 OpenWrt
# Author: Dirk Chang <dirk@kooiot.com>
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qt5websockets
PKG_VERSION:=5.15.0
PKG_RELEASE:=2
PKG_HASH:=87c2f6542778f9b65b3f208740c1d0db643fd0bede21404b9abb265355da5092

PKG_SYS_NAME:=qtwebsockets-everywhere-src-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SYS_NAME).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/$(basename $(PKG_VERSION))/$(PKG_VERSION)/submodules

PKG_BUILD_DIR=$(BUILD_DIR)/$(PKG_SYS_NAME)
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DEPENDS:=qt5base
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
-include $(STAGING_DIR)/host/mk/qmake.mk

define Package/qt5websockets
  SECTION:=video-frameworks
  CATEGORY:=Video
  SUBMENU:=Frameworks and Toolkits
  TITLE:=qt5websockets
  URL:=http://qt.io
  DEPENDS:=+qt5base-core +qt5base-network +qt5quick2-qml
endef

define Build/InstallDev
	$(call Build/Install/HostFiles,$(1))
	$(call Build/Install/Headers,$(1))
	$(call Build/Install/Libs,$(1),*)
endef

define Package/qt5websockets/install
	$(call Build/Install/Libs,$(1),libQt5WebSockets)

	$(INSTALL_DIR) \
	  $(1)/usr/lib/qt5/qml/QtWebSockets

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/qt5/qml/QtWebSockets/* \
	  $(1)/usr/lib/qt5/qml/QtWebSockets/
endef

$(eval $(call BuildPackage,qt5websockets))
