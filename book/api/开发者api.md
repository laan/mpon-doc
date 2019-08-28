### 1.0  账号登录
#### 1.1说明
获取session_key

#### 1.2请求方式
|接口详情||
|--|--|
|地址|/developer/login/|
|请求方式|get|

#### 1.3请求参数
| 参数 | 是否必填 | 类型|说明 |
| ---- | -------- |---|----|
|username|是|str|账号|
|pwd|是|str|密码(md5一次)|

#### 1.4返回结果
```json
{
    "code": 200,
    "data": {
        "session_key": "82elqy0ryr68wq3ezdg1974lf7819658",
        }
}

```
#### 1.5字段说明
| 返回值 | 类型 | 说明 |
| ---- | -------- |---|
|code|int|200:成功 非200:失败|
|error_msg|str|返回失败错误信息|
|data|obj|返回成功的数据体|
|session_key|str|session_key作其他接口验证使用|


### 2.0 开发者接口验证签名算法

#### 2.1 说明
开发者的其他接口必须使用该接口验证

#### 2.2需要参数
| 参数 | 是否必填 | 类型|说明 |
| ---- | -------- |---|----|
|username|是|str|账号|
|session_key|是|str|登录获取的session_key|
|`__md5`|是|str|md5的key生成方法如下|
|ts|是|str|时间戳(单位:秒)|

#### 2.3 __md5 生成方式

1，将除带`__`开头外的所有参数按key进行字典升序排列。注：以`__`开头的参数不参与签名

2、将第1步中排序后的参数(key=value)用&拼接起来；
除请求参数外还需把 'developer_login' 作为签名参数用'&’符号连接,放置最末；
如:session_key=dfdfdffeel&ts=1111&username=55512&developer_login

3、将第2步的排列好的字符串，md5进行加密；
如: ''c30ff12d83df678ae4499d4098a1b0cc'

### 3.0 获取游戏列表
#### 3.1 说明
获取账号下所有开发者的游戏列表
#### 3.2请求方式
|接口详情||
|--|--|
|地址|/developer/game_list/|
|请求方式|get|
#### 3.3请求参数
| 参数 | 是否必填 | 类型|说明 |
| ---- | -------- |---|----|
|username|是|str|账号|
|session_key|是|str|登录获取的session_key(见1.0)|
|`__md5`|是|str|md5的key(见2.0)|
|ts|是|str|时间戳(单位:秒)|

#### 3.4返回结果
```json
{
    "data": 
        {
            "game_list": [
                {
                    "game_id": 9,
                    "game_name": "红颜养成记",
                 	"game_icon":"http://127.0.0.1:8000/media/game_icon/3cc5.png",
                    "info": "盛宠在身，你会选择成为贤妃还是佞妃？",
                    "portrait": 2,
                    "player_num": "778万人玩过",
                    "online_version": {
                        "version_id": 11,
                        "version_num": "1.00",
                        "version_info": "红颜养成记",
                        "version_file":"http://127.0.0.1:8000/media/version_file/4c2.zip",
                        "version_file_md5": "07d31db12598d699f0095b119ba6639c"
                    },
                    "check_version": {
                        "version_id": 11,
                        "version_num": "1.00",
                        "version_info": "红颜养成记",
                        "version_file": "http://127.0.0.1:8000/media/version_file/4c2.zip",
                        "version_file_md5": "07d31db12598d699f0095b119ba6639c",
                        "check_status":1
                    },
                    "test_version": {
                        "version_id": 11,
                        "version_num": "1.00",
                        "version_info": "红颜养成记",
                        "version_file": "http://127.0.0.1:8000/media/version_file/4c2.zip",
                        "version_file_md5": "07d31db12598d699f0095b119ba6639c"
                    },
                    "roll_version": {
                        "version_id": 11,
                        "version_num": "1.00",
                        "version_info": "红颜养成记",
                        "version_file": "http://127.0.0.1:8000/media/version_file/4c2.zip",
                        "version_file_md5": "07d31db12598d699f0095b119ba6639c"
                    }         
                }
            ]
        }
    ,
    "code": 200
}
```
#### 3.5字段说明
| 返回值 | 类型 | 说明 |
| ---- | -------- |---|
|code|int|200:成功 非200:失败|
|error_msg|str|返回失败错误信息|
|data|obj|返回成功的数据体|
|developer_id|int|开发者id|
|developer_name|str|开发者name|
|game_id|int|游戏id|
|game_name|str|游戏名|
|game_icon|str|游戏图标|
|player_num|str|多少人玩过|
|info|str|游戏说明|
|portrait|int|1:横屏 2:竖屏|
|online_version|obj|上线版本|
|check_version|obj|审核版本|
|test_version|obj|测试版本|
|roll_version|obj|回滚版本|
|check_status|int|1:审核中 2:审核通过 3:审核拒绝(只有审核版本才有)|
|version_id|int|版本id|
|version_num|str|版本号|
|version_info|str|版本号说明|
|version_file|str|版本号文件url|
|version_file_md5|str|版本文件md5值|

