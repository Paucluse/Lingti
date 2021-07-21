#
# Copyright (C) 2021 Paucluse
#
# This is free software, licensed under the GNU General Public License v3.
#

#
# 
# 
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lingtigamebooster
PKG_VERSION:=v1.4.4
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=@(aarch64||arm||mipsel||x86_64) +kmod-tun
	TITLE:=Lingti's Game Booster
	URL:=https://lingti.com
endef

define Package/$(PKG_NAME)/description
Lingti's  Game Booster Accelerates Triple-A Gameplay and Market
endef

ifeq ($(ARCH),x86_64)
	Lingti_ARCH:=x86_64
	PKG_MD5SUM:=16620ba59dc52a52705e2be8c38d994a
endif

ifeq ($(ARCH),mipsel)
	Lingti_ARCH:=mipsel
	PKG_MD5SUM:=e72e9fa1761648113e9437f0e438f801
endif

ifeq ($(ARCH),arm)
	Lingti_ARCH:=arm
	PKG_MD5SUM:=3c24b9c6fceab1d2b08dfd3bd027fdf5
endif

ifeq ($(ARCH),aarch64)
	Lingti_ARCH:=aarch64
	PKG_MD5SUM:=01be691af0a2e856be80754d49fa821a
endif

PKG_SOURCE_URL:=http://lingti-1302055788.file.myqcloud.com/router/$(PKG_VERSION)/lingti-router-$(Lingti_ARCH).tar.gz?

#http://uu.gdl.netease.com/uuplugin/openwrt-$(UU_ARCH)/$(PKG_VERSION)/uu.tar.gz?
PKG_SOURCE:=$(PKG_NAME)-$(Lingti_ARCH)-$(PKG_VERSION).tar.gz

STRIP:=true

UNTAR_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/$(PKG_NAME)-$(Lingti_ARCH)-bin

define Build/Prepare
	mkdir -vp $(UNTAR_DIR)
	tar -zxvf $(DL_DIR)/$(PKG_SOURCE) -C $(UNTAR_DIR)
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	# $(INSTALL_DIR) $(1)/etc/init.d
	# $(INSTALL_BIN) ./files/uugamebooster.init $(1)/etc/init.d/uuplugin

	$(INSTALL_DIR) $(1)/usr/share/$(PKG_NAME)
	$(INSTALL_BIN) $(UNTAR_DIR)/lingti $(1)/usr/share/$(PKG_NAME)/lingti
	# $(INSTALL_CONF) $(UNTAR_DIR)/uu.conf $(1)/usr/share/$(PKG_NAME)/uu.conf

	# not finish yet:
	# $(INSTALL_DIR) $(1)/usr/bin
	# $(INSTALL_BIN) ./files/uugamebooster-update $(1)/usr/bin/$(PKG_NAME)
	# $(LN) $(1)/usr/bin/$(PKG_NAME)/uugamebooster-update $(1)/usr/bin/uugamebooster-update
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
