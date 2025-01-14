# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2024  0xACE8
# 
# This is free software, licensed under the Apache License, Version 2.0 .


include $(TOPDIR)/rules.mk

PKG_NAME:=ddns-go
PKG_VERSION:=6.7.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/jeessy2/ddns-go/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=2f376b807c72c902f2e1a8a231acf20c4ecb92881c76352cd8144f3fa5ed7a81

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/jeessy2/ddns-go/v6

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/ddns-go
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  TITLE:=Simple and easy-to-use Dynamic DNS client
  URL:=https://github.com/jeessy2/ddns-go
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
  USERID:=ddns-go:ddns-go
endef

define Package/ddns-go/description
  ddns-go is a automatically obtain your public IPv4 or IPv6 address and resolve it to the corresponding domain name service,
  support Alidns Dnspod Cloudflare Hicloud Callback Baiducloud porkbun GoDaddy Google Domains.
endef

define Package/ddns-go/install
	$(call GoPackage/Package/Install/Bin,$(1))

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(CURDIR)/file/ddns-go.init $(1)/etc/init.d/ddns-go

	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) $(CURDIR)/file/luci-ddns-go.uci-default $(1)/etc/uci-defaults/luci-ddns-go
endef

$(eval $(call GoBinPackage,ddns-go))
$(eval $(call BuildPackage,ddns-go))
