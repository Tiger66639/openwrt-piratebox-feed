include $(TOPDIR)/rules.mk

PKG_NAME:=extendRoot
PKG_VERSION:=0.0.10
PKG_RELEASE:=1


include $(INCLUDE_DIR)/package.mk

define Package/extendRoot
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=extendRoot
#  SUBMENU:=
#DESCRIPTION:=This variable is obsolete. use the Package/name/description define instead!
  URL:=http://piratebox.aod-rpg.de/dokuwiki/doku.php/extendRoot
  DEPENDS:= +kmod-usb2 +kmod-usb-storage +kmod-fs-vfat +kmod-nls-cp437 +kmod-nls-cp850 +kmod-nls-iso8859-1 +kmod-nls-iso8859-15 +kmod-fs-ext4 +block-mount +kmod-loop +losetup 
  PKGARCH:=all
  MAINTAINER:=Matthias Strubel <matthias.strubel@aod-rgp.de>
endef

define Package/extendRoot/description
  Creates and extend-mount-point on USB-SDA1
endef


define Package/extendRoot/postinst
	#!/bin/sh
	. /etc/ext.config
	# don't run initialisation  if /tmp/ext_no_auto_ext exists
	if [ -e $$ext_no_install  ] ; then
	   echo "Doesn't run init because $$ext_no_install exists "
	   exit 0
	fi
	/etc/init.d/ext init
endef

define Package/extendRoot/prerm
	#!/bin/ssh
	#/etc/init.d/ext deinstall
endef

define Build/Compile
endef

define Build/Configure
endef


define Package/extendRoot/install
	$(INSTALL_DIR) $(1)/usr/share/ext
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/usr/share/ext/* $(1)/usr/share/ext/
	$(INSTALL_BIN) ./files/etc/init.d/* $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/etc/ext.config $(1)/etc/
endef

$(eval $(call BuildPackage,extendRoot))