#
# This software is licensed under the Public Domain.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dawn-nolibgcrypt
PKG_SOURCE_DATE:=2024-12-14
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/rikhwanto/DAWN-nogcrypt.git
PKG_SOURCE_VERSION:=0bd4bfe346285a614e2a8f855bf78c90245d3606
PKG_MIRROR_HASH:=a0fe795d0c3b7467712c89b6bf753a70e2851ec7d1f88b8256ee9215b982e258

PKG_MAINTAINER:=Ridhwan Ikhwanto <ridhwan@ikhwanto.com>
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_FLAGS:=no-lto

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/dawn-nolibgcrypt
  SECTION:=net
  CATEGORY:=Network
  TITLE:= noglibcrypt variant - Decentralized wifi controller
  URL:=https://github.com/berlin-open-wireless-lab/DAWN.git
  DEPENDS:=$(DRV_DEPENDS) +libubus +libubox +libblobmsg-json +libuci +libiwinfo +umdns
  PROVIDES:=dawn
  VARIANT:=nolibgcrypt
endef

define Package/dawn-nolibgcrypt/description
  This package implements a decentralized wireless daemon.
endef

define Package/dawn-nolibgcrypt/conffiles
/etc/config/dawn
endef

define Package/dawn-nolibgcrypt/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/dawn $(1)/usr/sbin/dawn
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/dawn.init $(1)/etc/init.d/dawn
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/dawn.config $(1)/etc/config/dawn
endef

$(eval $(call BuildPackage,dawn-nolibgcrypt))
