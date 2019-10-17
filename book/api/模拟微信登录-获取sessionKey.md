## 模拟微信登录获取sessionKey

### 1 登录
#### 1.1 说明

模拟微信登录获取sessionKey

#### 1.2请求方式
|接口详情||
|--|--|
|地址|/wx/session/|
|请求方式|get|
#### 1.3请求参数
| 参数 | 是否必填 | 类型|说明 |
| ---- | -------- |---|----|
|code|是|str|前端获取的code|

#### 1.4返回结果
```json
{
   "session_key":"4e12c927a4f5af38ac2376==",
   "openid":"321b69e40b19cb6833c0d8c1650bec41"
}

```
#### 1.5字段说明
| 返回值 | 类型 | 说明 |
| ---- | -------- |---|
|errcode|int|错误码|
|errmsg|str|错误信息|
|session_key|str|用于解密encrypted_data加密用户数据|
|openid|str|用户openid|

注:encrypted_data ，signature 加密算法同微信，解密时appid为固定值:"bearmob"
	[微信校验与解密开放数据文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/signature.html)

