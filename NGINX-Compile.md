./configure --user=nginx --group=nginx --prefix=/usr/local/nginx/ \
--with-cc-opt="-I/usr/local/opt/openssl/include/ -I/usr/local/opt/pcre/include/" \
--with-ld-opt="-L/usr/local/opt/openssl/lib/ -L/usr/local/opt/pcre/lib/" \
--with-http_ssl_module             \
--with-http_v2_module              \
--with-http_v3_module              \
--with-http_realip_module          \
--with-http_addition_module        \
--with-http_xslt_module            \
--with-http_image_filter_module    \
--with-http_sub_module             \
--with-http_dav_module             \
--with-http_flv_module             \
--with-http_mp4_module             \
--with-http_gunzip_module          \
--with-http_gzip_static_module     \
--with-http_auth_request_module    \
--with-http_random_index_module    \
--with-http_secure_link_module     \
--with-http_degradation_module     \
--with-http_slice_module           \
--with-http_stub_status_module     \
--with-stream                      \
--with-stream_ssl_module           \
--with-stream_realip_module        \
--with-stream_geoip_module         \
--with-stream_ssl_preread_module   \
-j4