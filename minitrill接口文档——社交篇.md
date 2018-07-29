# minitrill接口文档——社交篇

>创建时间：2018-07-24  
维护人员：曾凌峰，欧小靓  
版本：v1.0  

[TOC]

## 接口统一返回说明

```python
{
    "success" : true,
    "code" : 0 ,#错误码，0代表成功，其他代表失败
    "data" : { #数据字典
        "id" : 307,
        ...
    },
    "message" : "成功"  #提示消息
}
```


|code| 含义|
|----|-----|
|0   | 成功 |
|30  | 资源不存在|
|63  |没有权限请求该资源|
|54  |请求有误|  

待补充

## 接口详情

### 分享视频

``/api/v1.0/video/share/<int:video_id>``  
分享视频

请求类型  
PUT

请求参数  
无

返回示例
略

### 点赞视频

``/api/v1.0/video/like/<int:video_id>``  
分享视频

请求类型  
PUT

请求参数  
无

返回示例  
略


### 关注某人

``/api/v1.0/relation/<int:user_id>``  
为当前登陆账号关注uid为user_id的人

请求类型  
POST

请求参数  
无

返回示例  
略


### 取消关注某人

``/api/v1.0/relation/<int:user_id>``  
为当前登陆账号取消关注uid为user_id的人

请求类型  
DELETE

请求参数  
无

返回示例  
略


### 获取关注的人或者粉丝用户数据

``/api/v1.0/relation/?page=1&type=fan``  
获取当前登陆的人的粉丝或者关注人的用户数据，以分页形式获取，每次返回10条数据

请求类型  
GET

请求参数  

|参数名   |  类型 | 必填 | 描述|
|--------|-------|-----|------|
|type | enum(fan, master)| Yes |请求类型：type=fan表示请求粉丝，type=master表示请求关注者| 
|page | int| Yes |请求的页码，分页请求，每次返回10条以内的数据|

返回示例
```python
{
    "message": "成功",
    "code": 0,
    "data": [
        {
            "status": 0,
            "province": "保密",
            "account": "qqqqqq12",
            "tel": "保密",
            "uid": -6070221056220097789,
            "city": "保密",
            "country": "中国",
            "age": 18,
            "video_num": 0,
            "sex": "保密",
            "brief_introduction": "",
            "fans": 0,
            "video_like_num": 0,
            "birth": null,
            "follow": 0,
            "password": "",
            "nickname": "qqqqqq12",
            "register_date": "2018-07-21 18:18:02",
            "photo_url": "/data/minitrill/user/photo/default/default.jpg"
        },
        {
            "status": 0,
            "province": "保密",
            "account": "qqqqqq12",
            "tel": "保密",
            "uid": -6070221056220097789,
            "city": "保密",
            "country": "中国",
            "age": 18,
            "video_num": 0,
            "sex": "保密",
            "brief_introduction": "",
            "fans": 0,
            "video_like_num": 0,
            "birth": null,
            "follow": 0,
            "password": "",
            "nickname": "qqqqqq12",
            "register_date": "2018-07-21 18:18:02",
            "photo_url": "/data/minitrill/user/photo/default/default.jpg"
        },
        ...
    ],
    "success": true
}
```



### 发送私信

``/api/v1.0/message/``  
发送私信

请求类型  
POST

请求参数  

|参数名   |  类型 | 必填 | 描述|
|--------|-------|-----|------|
|recive_uid | int| Yes |私信接收者| 
|text | String| Yes |私信文本|


返回示例  
略


### 删除私信

``/api/v1.0/message/<int:message_id>``  
删除id为message_id的私信

请求类型  
DELETE

请求参数  
无

返回示例  
略


### 获取私信数据

``/api/v1.0/message/?page=1&type=send``  
获取当前登陆的人的私信数据，以分页形式获取，每次返回10条数据

请求类型  
GET

请求参数 

|参数名   |  类型 | 必填 | 描述|
|--------|-------|-----|------|
|type | enum(send, recive, unreadnum)| Yes |请求类型：type=send表示请求自己发送的私信，type=recive表示请求接受的私信，unread表示请求未读私信数量| 
|page | int| Yes |请求的页码，分页请求，每次返回10条以内的数据|

返回示例  
略


### 把私信标记为已读

``/api/v1.0/message/<int:message_id>``  
把id为message_id的私信标记为已读

请求类型  
PUT

请求参数 
无

返回示例  
略