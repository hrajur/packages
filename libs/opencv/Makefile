#
# Copyright (C) 2013-2014 wrtnode.com
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=opencv
PKG_VERSION:=2.4.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).zip
PKG_SOURCE_URL:=http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.4.10/
PKG_MD5SUM:=ec63952d3a3dff965d5fdde765926821

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk


define Package/opencv/Default/description
 OpenCV (Open Source Computer Vision Library) is an open source computer
 vision and machine learning software library. OpenCV was built to provide
 a common infrastructure for computer vision applications and to accelerate
 the use of machine perception in the commercial products. Being a
 BSD-licensed product, OpenCV makes it easy for businesses to utilize
 and modify the code.
endef

define Package/opencv
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=opencv-2.4.10
  URL:=http://opencv.org/
  MAINTAINER:=WRTnode Team <pub@wrtnode.com>
  DEPENDS:=+libpthread +librt +libstdcpp +zlib +libjpeg
endef


PKG_INSTALL:=1

CMAKE_OPTIONS += -DBUILD_opencv_gpu:BOOL=OFF \
	 -DWITH_1394:BOOL=OFF -DBUILD_opencv_stitching:BOOL=OFF \
	 -DBUILD_opencv_superres:BOOL=OFF -DBUILD_opencv_ts:BOOL=OFF

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/opencv $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/opencv2 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopencv* $(1)/usr/lib/
endef

define Package/opencv/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopencv* $(1)/usr/lib/

endef

$(eval $(call BuildPackage,opencv))
