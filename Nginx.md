```text
user root;
worker_processes  2;
error_log  /var/logs/nginx/error.log notice;
events {
    worker_connections  1024;
}
http {
    include       conf.d/mime.types;
    default_type  application/octet-stream;
    add_header Cross-Origin-Embedder-Policy "require-corp" always;
    add_header Cross-Origin-Opener-Policy   "same-origin"  always;
    server {
        listen       8080 ssl;
        server_name  www.monostarsky.com;
        ##
        ##  openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /path/to/monostarsky.key -out /path/to/monostarsky.crt
        ##
        ssl_certificate      /path/to/monostarsky.crt;
        ssl_certificate_key  /path/to/monostarsky.key;

        ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;

        ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers  on;

        # 文件下载入口: http://xxx.com/download
        location / {
            root  /path/webSite/files;
              
            autoindex on;
            autoindex_localtime on; 
        }         
    }
}
```

```shell
nginx -c /path/to/private-nginx.conf
