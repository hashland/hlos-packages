include $(TOPDIR)/rules.mk

PKG_NAME:=hlos-utils
PKG_RELEASE:=1

PKG_MAINTAINER:=Julian Haupt <julian.haupt@hashland.cc>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/hlos-utils
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Hashland OS Utilities
	DEPENDS:=+opkg +hl-cli +libubox
endef

Build/Compile=

define Package/hlos-utils/conffiles
/etc/config/hlos
endef

define Package/hlos-utils/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(FILES_DIR)/pkgupgrade $(1)/sbin/pkgupgrade
	$(INSTALL_BIN) $(FILES_DIR)/fw_setdefaultenv $(1)/sbin/fw_setdefaultenv
	$(INSTALL_BIN) $(FILES_DIR)/hlos-update $(1)/sbin/hlos-update
	$(INSTALL_BIN) $(FILES_DIR)/hlos-update.init          $(1)/etc/init.d/hlos-update
endef

$(eval $(call BuildPackage,hlos-utils))
