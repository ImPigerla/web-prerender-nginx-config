Web预渲染 + 路由history模式 + Nginx配置

如下是nginx的配置

```js
server {
    # 端口号
    listen 4443;
    
    # 服务器/域名
    server_name localhost;

    index index.html index.htm;

    # 静态文件路径
    root /这里是静态文件的访问路径;

    # 所有路径
    location / {
        try_files $uri $uri/ @rewrites;
    }

    # 当找不到静态文件的处理
    location @rewrites {
        rewrite ^\/(.*)\/.*?  /$1/index.html last;
    }
}
```

正则例子，可访问[https://regexr.com/45pfu](https://regexr.com/45pfu)
