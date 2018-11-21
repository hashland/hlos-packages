include $(TOPDIR)/rules.mk

PKG_NAME:=hlos-update
PKG_RELEASE:=1

PKG_MAINTAINER:=Julian Haupt <julian.haupt@hashland.cc>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/hlos-update
  SECTION:=base
  CATEGORY:=Base system
  TITLE:=Hashland OS Updater
  DEPENDS:=+opkg +hl-cli +libubox
endef

Build/Compile=

define Package/hlos-update/conffiles
/etc/config/hlos
endef

define Package/hlos-update/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(FILES_DIR)/pkgupgrade $(1)/sbin/pkgupgrade
	$(INSTALL_BIN) $(FILES_DIR)/hlos-update $(1)/sbin/hlos-update
	$(INSTALL_BIN) $(FILES_DIR)/hlos-update.init          $(1)/etc/init.d/hlos-update
endef

$(eval $(call BuildPackage,hlos-update))
