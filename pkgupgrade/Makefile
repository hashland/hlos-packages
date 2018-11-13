include $(TOPDIR)/rules.mk

PKG_NAME:=pkgupgrade
PKG_RELEASE:=3

PKG_MAINTAINER:=Julian Haupt <julian.haupt@hashland.de>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/pkgupgrade
  SECTION:=base
  CATEGORY:=Base system
  TITLE:=Package upgrader
  DEPENDS:=+opkg
endef

Build/Compile=

define Package/node-hlminer/conffiles
/etc/config/pkgupgrade
endef

define Package/pkgupgrade/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(FILES_DIR)/pkgupgrade $(1)/sbin/pkgupgrade
	$(INSTALL_BIN) $(FILES_DIR)/pkgupgrade.init           $(1)/etc/init.d/pkgupgrade
	$(CP)          $(FILES_DIR)/pkgupgrade.config         $(1)/etc/config/pkgupgrade
endef

$(eval $(call BuildPackage,pkgupgrade))
