# 这是 nodejs-blog 对应的前端页面, 页面简陋, 仅做测试接口用

Node.js 博客后台地址: [nodejs-blog](https://github.com/liguoyou/nodejs-blog)

## 运行

```
npm install http-server -g

npm server -p 3001
```

### 此外还需要做, nginx 做反向代理配置

```bash
listen 8080;

# code...
# 中间是原来的东东
# code...

# 这里注释了原来的配置
# location / {
#   root   html;
#   index  index.html index.htm;
# }

location / {
	proxy_pass http://localhost:3001;
}

location /api/ {
	proxy_pass http://localhost:3000;
	proxy_set_header Host $host;
}
```

3000 是 nodejs 接口服务的端口

参考/来源: [前端晋升全栈工程师必备课程 Node.js 从零开发 web server 博客项目](https://coding.imooc.com/class/320.html)
