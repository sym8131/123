include $(TOPDIR)/rules.mk

PKG_NAME:=libtracefs
PKG_VERSION:=1.7.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://git.kernel.org/pub/scm/libs/libtrace/libtracefs.git/snapshot/
PKG_HASH:=411fcbf3434ecbaefa6c2b1bf092266293a672e2d7ee46fdd6b402753cb8bd16

PKG_MAINTAINER:=Nick Hainke <vincent@systemli.org>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libtracefs
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Linux kernel trace file system library
  URL:=https://git.kernel.org/pub/scm/libs/libtrace/libtracefs.git
  DEPENDS+=+libpthread +libtraceevent
  ABI_VERSION:=0
endef

define Package/libtracefs/description
The libtracefs library provides APIs to access kernel trace file system.
endef

CONFIGURE_ARGS+= \
	--enable-shared \
	--enable-static \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_BUILD_DIR)/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/lib/libtracefs.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_BUILD_DIR)/libtracefs.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libtracefs/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/lib/libtracefs.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtracefs))
