#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-gmpy2
PKG_VERSION:=2.0.8
PKG_RELEASE:=3

PKG_SOURCE:=gmpy2-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/source/g/gmpy2
PKG_HASH:=dd233e3288b90f21b0bb384bcc7a7e73557bb112ccf0032ad52aa614eb373d3f

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-gmpy2-$(PKG_VERSION)

PKG_LICENSE:=LGPL-3.0+
PKG_LICENSE_FILES:=COPYING.LESSER
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PKG_UNPACK:=unzip -q -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE); mv -f $(PKG_BUILD_DIR)/gmpy2-$(PKG_VERSION)/* $(PKG_BUILD_DIR)

PYTHON_PKG_SETUP_ARGS:=--nompfr
PYTHON3_PKG_SETUP_ARGS:=--nompfr

define Package/python-gmpy2/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=GMP/MPIR, MPFR, and MPC interface
  URL:=https://github.com/aleaxit/gmpy
  DEPENDS:=+libgmp
endef

define Package/python-gmpy2
$(call Package/python-gmpy2/Default)
  DEPENDS+=+PACKAGE_python-gmpy2:python-light
  VARIANT:=python
endef

define Package/python3-gmpy2
$(call Package/python-gmpy2/Default)
  DEPENDS+=+PACKAGE_python3-gmpy2:python3-light
  VARIANT:=python3
endef

define Package/python-gmpy2/description
gmpy2 is a C-coded Python extension module that supports multiple-precision
arithmetic. gmpy2 is the successor to the original gmpy module. The gmpy module
only supported the GMP multiple-precision library. gmpy2 adds support for the
MPFR (correctly rounded real floating-point arithmetic) and MPC (correctly
rounded complex floating-point arithmetic) libraries. gmpy2 also updates the
API and naming conventions to be more consistent and support the additional
functionality.
endef

define Package/python3-gmpy2/description
$(call Package/python-gmpy2/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-gmpy2))
$(eval $(call BuildPackage,python-gmpy2))
$(eval $(call BuildPackage,python-gmpy2-src))

$(eval $(call Py3Package,python3-gmpy2))
$(eval $(call BuildPackage,python3-gmpy2))
$(eval $(call BuildPackage,python3-gmpy2-src))
