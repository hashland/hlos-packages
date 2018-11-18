include $(TOPDIR)/rules.mk

PKG_NAME:=hl-cli
PKG_VERSION:=git-$(shell git ls-remote https://github.com/hashland/hl-cli master | cut -f1 | cut -c1-7)
PKG_RELEASE:=1

PKG_REV:=master
PKG_SOURCE_URL:=git://github.com/hashland/hl-cli.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_MAINTAINER:=Julian Haupt <julian.haupt@hashland.cc>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/hl-cli
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Hashland Command Line Interface
	DEPENDS:=+curl +jq
endef

Build/Compile=

define Package/hl-cli/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/hl $(1)/usr/bin/hl
endef

$(eval $(call BuildPackage,hl-cli))
