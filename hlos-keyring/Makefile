include $(TOPDIR)/rules.mk

PKG_NAME:=hlos-keyring
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/hashland/hlos-keyring.git
PKG_SOURCE_DATE:=2018-11-13
PKG_SOURCE_VERSION:=5dbffe1c93519d64bab7e1088386b3b02c678e66
PKG_MIRROR_HASH:=239b00693be9c54c498909f279b4c59a043cf3108536eb6494c338770109e3e5

PKG_MAINTAINER:=Julian Haupt <julian.haupt@hashland.cc>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

define Package/hlos-keyring
  SECTION:=base
  CATEGORY:=Base system
  PROVIDES:=openwrt-keyring
  TITLE:=Hashland OS Developer Keyring
endef

Build/Compile=

define Package/hlos-keyring/install
	$(INSTALL_DIR) $(1)/etc/opkg/keys/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/usign/* $(1)/etc/opkg/keys/
endef

$(eval $(call BuildPackage,hlos-keyring))
