include $(TOPDIR)/rules.mk

PKG_NAME:=sgminer

PKG_VERSION:=git-$(shell git ls-remote https://github.com/hashland/sgminer-baikal dev | cut -f1 | cut -c1-7)
PKG_REV:=dev

PKG_RELEASE:=1
PKG_INSTALL:=1

PKG_SOURCE_URL:=git://github.com/hashland/sgminer-baikal.git
PKG_SOURCE_PROTO:=git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_REV).tar.bz2

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_FIXUP:=autoreconf
PKG_CHECK_FORMAT_SECURITY:=0

include $(INCLUDE_DIR)/package.mk

define Package/sgminer
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=sgminer
	URL:=https://github.com/hashland/sgminer-baikal
	DEPENDS:=+libcurl +libpthread +jansson +libusb-1.0
endef

define Package/sgminer/description
Sgminer is a multi-threaded multi-pool GPU, FPGA and CPU miner with ATI GPU
monitoring, (over)clocking and fanspeed support for bitcoin and derivative
coins. Do not use on multiple block chains at the same time!
endef

TARGET_LDFLAGS += -Wl,-rpath-link=$(STAGING_DIR)/usr/lib

CONFIGURE_ARGS += --disable-udev --disable-git-version --with-system-libusb --without-curses

define Build/Compile
	$(call Build/Compile/Default)
endef

define Package/sgminer/install
	$(INSTALL_DIR) $(1)/usr/bin

	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sgminer  $(1)/usr/bin
endef

$(eval $(call BuildPackage,sgminer))
