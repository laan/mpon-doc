## 模拟微信登录获取code

### 1 登录
#### 1.1 说明

模拟微信登录获取code

#### 1.2请求方式
|接口详情||
|--|--|
|地址|/wx/login/|
|请求方式|get|
#### 1.3请求参数
| 参数 | 是否必填 | 类型|说明 |
| ---- | -------- |---|----|
|uid|是|str|用户设备码|

#### 1.4返回结果
```json
{
    "code":200,
    "data":{
        "iv":"b60c1542cb6446d8740da8==",
        "encrypted_data":"aTDGVzQ80L031Pm9j07Q61nJvUjfUvoH93nVuYPqvDsLu+iFvQC3jFl7nRJIUucHpNxgfuqSlJVUKkU4Vus9hUaY3+V5YMV49QexXjqVof6ssDXqHnNLOjsamHKUctTbRFeJYBMMn1WfNCEvmMqK6TFp4lY5acuHX6FX7CX5gD+7I5UdCAY4mnga+avhyljCM9meKkbpoEjTJAcbgtrjJwox4/45Nbq2mwMxC1w2ydJomGl6yAU8WuqonGzr8hcVLu3fB7vV9H3lZFgf5Bkg96CFifA4WGWvBU0euHnjbiw2m9STAk5z0a2S1gdZCGET/+YXLvI9UIYdqnyEG3fZqoYnHS4N/X4Bx1oUa8U+F3M=",
        "raw_data":{
            "avatarUrl":"http://127.0.0.1:8000/static/media/random_avatar/1571022753.png",
            "nickName":"祝蓉志",
            "gender":1,
            "language":"zh_CN",
            "city":"",
            "province":"",
            "country":""
        },
        "signature":"55f4d1bc845fd71db8795f2d51bb2374",
        "code":"MTU3MTAzNzAyNy40MzM4ODg0OjU3ZTAyMmRhMGU4MzlmNDRkMjk5OGQ3ZDYzMTQ3NWZhZDE3MzkwNDA6MDAwMDAwMDAtMGJhYy1jMWU2LWZmZmYtZmZmZmVmMDVhYzRh"
    }
}

```
#### 1.5字段说明
| 返回值 | 类型 | 说明 |
| ---- | -------- |---|
|code|int|200:成功 非200:失败|
|error_msg|str|返回失败错误信息|
|data|obj|返回成功的数据体|
|iv|str|用于解密encrypted_data加密数据|
|encrypted_data|str|用户加密数据|
|raw_data|obj|用户明文数据|
|avatarUrl|str|用户头像|
|nickName|str|用户昵称|
|gender|int|性别(1:男，0:女)|
|language|str|语言|
|city|str|城市|
|province|str|省|
|country|str|国家|
|signature|str|签名数据|
|code|str|code用于获取sessionKey|
