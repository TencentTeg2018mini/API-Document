# minitrill接口文档——视频篇


>创建时间：2018-07-20  
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

### 获取标签 ok

``/api/v1.0/video/tag``  
请求所有视频标签

请求类型  
GET

请求参数  
无

返回示例

```python
{
    "message": "成功",
    "code": 0,
    "data": [
        "动画",
        "生活",
        "游戏",
        "娱乐",
        "体育",
        "纪录",
        "鬼畜",
        "音乐",
        "国创",
        "文学",
        "舞蹈",
        "科技",
        "广告",
        "影视",
        "时尚",
        "TV剧",
        "天文",
        "八卦"
    ],
    "success": true
}
```

### 设置喜爱视频标签 ok

``/api/v1.0/video/favoritetag``  
请求当前用户喜爱的所有视频标签

请求类型  
POST

请求参数  

|参数名|类型|必填|描述|默认值|参考值|  
|-----|----|----|----|---|----|
|tags|list|Yes|标签列表|无|lablabla|

参考示例

```python
{
    'tags':[
        "八卦",
        "体育",
        "动画",
        ...
    ]
}
```

返回示例
略


### 获取喜爱视频标签 

``/api/v1.0/video/favoritetag``  
请求当前用户喜爱的所有视频标签

请求类型  
GET

请求参数  
无

返回示例

```python
{
    "message": "成功",
    "code": 0,
    "data": [
        "体育",
        "八卦"
    ],
    "success": true
}
```

### 获取视频 ok

``/api/v1.0/video/video?page=1``  
请求视频资源

请求类型  
GET

请求参数  

|参数名|类型|必填|描述|
|-----|----|---|----|
|page | int| Yes |请求的页码，分页请求，每次返回5条以内的数据|

返回示例

```python
{
    "message": "成功",
    "code": 0,
    "data": [
        {
            "status": 1,
            "comment": 1506,
            "upload_time": "2018-07-26 10:11:13",
            "`like`": 12001,
            "vid": 1,
            "title": "Star Wars_ The Clone Wars Official Trailer",
            "tag2_id": 0,
            "v_photo_url": null,
            "share": 450,
            "tag3_id": 0,
            "note": "TEST",
            "flag": 1,
            "tag": "Star Wars",
            "uploader_nickname": "sw",
            "v_url": "/root/data/minitrill/video/deal1.mp4",
            "tag1_id": 0,
            "uploader_uid": 2,
            "view": 1306074
        },
        ...
    ],
    "success": true
}
```


### 发布评论 ok

``/api/v1.0/video/videocomment/<int:video_id>``  
对id为video_id的视频发布评论

请求类型  
POST

请求参数  

|参数名|类型|必填|描述|默认值|参考值|
|-----|----|----|----|---|----|
|comment|string|Yes|评论内容|无|双击666|
|ref_comment_id|int|No|引用的评论id|无|无|

参考示例

```python
{
    "comment":"lailailai",
    "ref_comment_id": ""
}
```

返回示例
略


### 获取评论 ok

``/api/v1.0/video/videocomment/``  
对id为video_id的视频发布评论

请求类型  
GET

请求参数  
无

返回示例

```python
{
    "message": "成功",
    "code": 0,
    "data": [
        {
            "status": 0,
            "comment": "跟到底跟到底",
            "comment_like": 5,
            "uid": -840729673,
            "vid": 3,
            "comment_id": 2,
            "comment_time": "2018-07-27 16:27:13",
            "ref_comment_id": 1
        },
        {
            "status": 0,
            "comment": "双击666送豪华游艇",
            "comment_like": 0,
            "uid": -840729673,
            "vid": 3,
            "comment_id": 1,
            "comment_time": "2018-07-27 16:24:26",
            "ref_comment_id": -1
        },
        ...
    ],
    "success": true
}
```


### 删除评论

``/api/v1.0/videocomment/<int:comment_id>``  
删除id为comment_id的评论

请求类型  
POST

请求参数    
无

返回实例  
略

### 点赞评论

``/api/v1.0/videocomment/<int:comment_id>``  
点赞id为comment_id的评论

请求类型  
PUT

请求参数    
无

返回实例  
略
