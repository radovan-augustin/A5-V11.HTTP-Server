#
# Copyright (c) 2015 Radovan Augustin, rado_augustin@yahoo.com
# All rights reserved.
#
# This file is licensed under BSD 3-Clause License.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nginx
PKG_VERSION:=1.9.5
PKG_RELEASE:=1

PKG_NAME_VERSION:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME_VERSION).tar.xz

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/nginx
  TITLE:=$(PKG_NAME_VERSION) HTTP server.
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libpthread +zlib
endef

define Package/nginx/description
  nginx HTTP server.
endef

define Build/Prepare
	$(TAR) -xJf ./src/$(PKG_SOURCE) -C $(BUILD_DIR)
endef

define Build/Configure
	cd $(PKG_BUILD_DIR) && ./configure \
                    --without-http_charset_module \
                    --without-http_ssi_module \
                    --without-http_userid_module \
                    --without-http_access_module \
                    --without-http_auth_basic_module \
                    --without-http_autoindex_module \
                    --without-http_geo_module \
                    --without-http_map_module \
                    --without-http_split_clients_module \
                    --without-http_referer_module \
                    --without-http_rewrite_module \
                    --without-http_proxy_module \
                    --without-http_fastcgi_module \
                    --without-http_uwsgi_module \
                    --without-http_scgi_module \
                    --without-http_memcached_module \
                    --without-http_limit_conn_module \
                    --without-http_limit_req_module \
                    --without-http_empty_gif_module \
                    --without-http_browser_module \
                    --without-http_upstream_hash_module \
                    --without-http_upstream_ip_hash_module \
                    --without-http_upstream_least_conn_module \
                    --without-http_upstream_keepalive_module \
                    --without-http_upstream_zone_module \
                    --without-http-cache \
                    --without-mail_pop3_module \
                    --without-mail_imap_module \
                    --without-mail_smtp_module \
                    --without-stream_limit_conn_module \
                    --without-stream_access_module \
                    --without-stream_upstream_hash_module \
                    --without-stream_upstream_least_conn_module \
                    --without-stream_upstream_zone_module \
                    --conf-path=/usbstorage/nginx/nginx.conf \
                    --error-log-path=/tmp/nginx/error.log \
                    --pid-path=/tmp/nginx/nginx.pid \
                    --lock-path=/tmp/nginx/nginx.lock \
                    --http-log-path=/tmp/nginx/access.log \
                    --http-client-body-temp-path=/tmp/nginx/client_body_temp \
                    --with-cc-opt='-DTCP_FASTOPEN=23 -DAT_EMPTY_PATH=0x1000 -DO_PATH=010000000'
endef

define Package/nginx/install
	$(STRIP) $(PKG_BUILD_DIR)/objs/nginx
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/objs/nginx $(1)/usr/sbin
endef

$(eval $(call BuildPackage,nginx))
