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

### 获取标签

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

### 设置喜爱视频标签

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

### 获取视频

``/api/v1.0/video/video/<int:vid>?page=1&uid=1324``  
请求视频资源

请求类型  
GET

请求参数  

|参数名   |  类型 | 必填 | 描述|
|--------|-------|-----|------|
|vid | int| No |请求具体的vid视频|
|page | int| Yes |请求的页码，分页请求，每次返回5条以内的数据|
|uid | int| no |请求的用户id，请求某个用户下的所有视频，按page分页|

返回示例

```python
{
    "message": "成功",
    "code": 0,
    "data": [
        {
            "comment": 3795,
            "tag2_id": null,
            "vid": 6496318021483629838,
            "share": 817,
            "tag": "美女",
            "tag1_id": null,
            "upload_time": "2018-08-11 17:07:14",
            "title": "另一个！！脸上是胎记！生下来就会的.",
            "v_photo_url": null,
            "note": "",
            "v_url": "/data/minitrill/video/6496318021483629838.mp4",
            "latitude": "22.5357697160",
            "uploader_nickname": "我是节操",
            "uploader_uid": 5752478763024436919,
            "status": 0,
            "tag3_id": null,
            "flag": 0,
            "address": "白石路, 大冲, 蛇口, 珠光村, 南山区, 深圳市, 广东省, 518000, 中国",
            "douyin_url": "https://aweme.snssdk.com/aweme/v1/play/?video_id=193f345cd7fe4347aa12c8db8f2379d3&line=0&ratio=720p&watermark=1&media_type=4&vr_type=0&test_cdn=None&improve_bitrate=0&logo_name=aweme",
            "like": 96153,
            "longitude": "113.9439215560",
            "geohash": "ws100ye2mg",
            "view": 0
        },
        ...
    ],
    "success": true
}
```


### 获取附近的视频

``/api/v1.0/neighbour/video?page=1&longitude=1324&latitude=123123&level=8``  
请求附近的视频资源

请求类型  
GET

请求参数  

|参数名   |  类型 | 必填 | 描述|
|--------|-------|-----|------|
|page | int| Yes |请求的页码，分页请求，每次返回5条以内的数据|
|longitude | str| Yes |经度坐标，字符长度在10以上|
|latitude | str| Yes |纬度坐标，字符长度在10以上|
|level | str| Yes |请求精度，具体说明如下|

level可取的值为1到10，分为不同的精度，建议取值6到8之间：

![level](https://note.youdao.com/yws/api/personal/file/87B592255A894081B4FDF8A086386E2C?method=download&shareKey=54b793525c90c75ddb612a05943aa744)

返回示例
 
略


### 发布评论

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


### 获取评论

``/api/v1.0/video/videocomment/<int:video_id>``  
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