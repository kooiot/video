#
# Copyright (C) 2020 OpenWrt
# Author: Mirko Vogt <mirko-openwrt@nanl.de>
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qt5quick2-controls
PKG_VERSION:=5.15.0
PKG_RELEASE:=1
PKG_HASH:=7072cf4cd27e9f18b36b1c48dec7c79608cf87ba847d3fc3de133f220ec1acee

PKG_SYS_NAME:=qtquickcontrols-everywhere-src-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SYS_NAME).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/$(basename $(PKG_VERSION))/$(PKG_VERSION)/submodules

PKG_BUILD_DIR=$(BUILD_DIR)/$(PKG_SYS_NAME)
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
-include $(STAGING_DIR)/host/mk/qmake.mk

define Package/qt5quick2-controls
  SECTION:=video-frameworks
  CATEGORY:=Video
  SUBMENU:=Frameworks and Toolkits
  TITLE:=qt5quick2-controls
  URL:=http://qt.io
  MAINTAINER:=Mirko Vogt <mirko-openwrt@nanl.de>
  DEPENDS:=+qt5quick2-quick +qt5base-widgets
endef

define Build/Install/QMLplugin
	$(INSTALL_DIR) \
	  $(1)/$(QT_INSTALL_QML)/$(2)

	$(CP) \
	  $(PKG_INSTALL_DIR)/$(QT_INSTALL_QML)/$(2)/{plugins.qmltypes,qmldir,$(3).{so,qml,js}*} \
	  $(1)/$(QT_INSTALL_QML)/$(2)/ \
	  || true
endef


define Package/qt5quick2-controls/install
	$(call Build/Install/QMLplugin,$(1),QtQuick/Controls,*)
	$(call Build/Install/QMLplugin,$(1),QtQuick/Dialogs,*)
	$(call Build/Install/QMLplugin,$(1),QtQuick/Extras,*)
	$(call Build/Install/QMLplugin,$(1),QtQuick/PrivateWidgets,*)
endef

$(eval $(call BuildPackage,qt5quick2-controls))
