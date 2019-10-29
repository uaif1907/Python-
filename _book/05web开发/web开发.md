#### 1. 简述同源策略
```
同源策略需要同时满足以下三点要求：
1）协议相同
2）域名相同
3）端口相同
 http:www.test.com与https:www.test.com 不同源——协议不同
 http:www.test.com与http:www.admin.com 不同源——域名不同
 http:www.test.com与http:www.test.com:8081 不同源——端口不同
 只要不满足其中任意一个要求，就不符合同源策略，就会出现“跨域”
```
#### 2. 简述cookie和session的区别
```
1，session 在服务器端，cookie 在客户端（浏览器）
2、session 的运行依赖 session id，而 session id 是存在 cookie 中的，也就是说，如果浏览器禁用了 cookie ，同时 session 也会失效，存储Session时，键与Cookie中的sessionid相同，值是开发人员设置的键值对信息，进行了base64编码，过期时间由开发人员设置
3、cookie安全性比session差
```
#### CSRF攻击
https://www.jianshu.com/p/67408d73c66d
#### SQL注入
https://www.jianshu.com/p/5c67414bfcb6
