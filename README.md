## 单点登录原理

[![](https://i.loli.net/2018/05/06/5aeeb3f76e521.png)](https://i.loli.net/2018/05/06/5aeeb3f76e521.png)

## 实现简介

- ### sso-client

1. 拦截子系统未登录用户请求，跳转至sso认证中心
2. 接收并存储sso认证中心发送的令牌
3. 与sso-server通信，校验令牌的有效性
4. 建立局部会话
5. 拦截用户注销请求，向sso认证中心发送注销请求
6. 接收sso认证中心发出的注销请求，销毁局部会话

- ### sso-server

1. 验证用户的登录信息
2. 创建全局会话
3. 创建授权令牌
4. 与sso-client通信发送令牌
5. 校验sso-client令牌有效性
6. 系统注册
7. 接收sso-client注销请求，注销所有会话
