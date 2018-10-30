# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=hlminer
PKG_NAME:=node-$(PKG_NPM_NAME)
PKG_VERSION:=git-$(shell git ls-remote https://github.com/hashland/hlminer master | cut -f1 | cut -c1-7)
PKG_RELEASE:=1

PKG_REV:=master
PKG_SOURCE_URL:=git://github.com/hashland/hlminer.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_BUILD_DEPENDS:=node/host
PKG_USE_MIPS16:=0

PKG_MAINTAINER:=Julian Haupt <julian.haupt@hashland.de>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/node-hlminer
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Hashland's Miner
  URL:=https://github.com/hashland/hlminer
  DEPENDS:=+node
endef

define Package/node-hlminer/description
 Hashland's crypto currency miner written in JavaScript.
endef

NODEJS_CPU:=$(subst powerpc,ppc,$(subst aarch64,arm64,$(subst x86_64,x64,$(subst i386,ia32,$(ARCH)))))

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(NODEJS_CPU) \
	npm_config_target_arch=$(NODEJS_CPU) \
	npm_config_build_from_source=true \
	npm_config_nodedir=$(STAGING_DIR)/usr/ \
	npm_config_prefix=$(PKG_INSTALL_DIR)/usr/ \
	npm_config_cache=$(TMP_DIR)/npm-cache \
	npm_config_tmp=$(TMP_DIR)/npm-tmp \
	npm install -g --production $(PKG_BUILD_DIR)
	rm -rf $(TMP_DIR)/npm-tmp
	rm -rf $(TMP_DIR)/npm-cache
endef

define Package/node-hlminer/conffiles
/etc/config/hlminer
endef

define Package/node-hlminer/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DIR) $(1)/usr/lib/node/$(PKG_NPM_NAME)
	$(INSTALL_BIN) $(FILES_DIR)/hlminer.init           $(1)/etc/init.d/hlminer
	$(CP)          $(FILES_DIR)/hlminer.config         $(1)/etc/config/hlminer
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/$(PKG_NPM_NAME)/{package.json,README.md,hlminer,miner,stratum} \
		$(1)/usr/lib/node/$(PKG_NPM_NAME)/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/$(PKG_NPM_NAME)/node_modules \
		$(1)/usr/lib/node/$(PKG_NPM_NAME)/
	$(LN) ../lib/node/$(PKG_NPM_NAME)/hlminer $(1)/usr/bin/hlminer

endef

$(eval $(call BuildPackage,node-hlminer))
