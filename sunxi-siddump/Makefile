include $(TOPDIR)/rules.mk

PKG_NAME:=sunxi-siddump
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/sunxi-siddump
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Sunxi Security ID Dump Tool
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	cp $(FILES_DIR)/* $(PKG_BUILD_DIR)
	$(Build/Patch)
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) -o $(PKG_BUILD_DIR)/sunxi-siddump.o -c $(PKG_BUILD_DIR)/sunxi-siddump.c
	$(TARGET_CC) $(TARGET_LDFLAGS) -o $(PKG_BUILD_DIR)/$1 $(PKG_BUILD_DIR)/sunxi-siddump.o
endef

define Package/sunxi-siddump/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sunxi-siddump $(1)/usr/sbin
endef

$(eval $(call BuildPackage,sunxi-siddump))

