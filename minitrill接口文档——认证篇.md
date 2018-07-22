# minitrill接口文档——认证篇


>创建时间：2018-07-18  
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

### 检查登录

``/api/v1.0/session``

请求类型  
GET

请求参数  
无

返回示例

```python
{
...
    "data" : {
        "islogin" : True,  #true表示已登录，false表示未登录，以下两项未空
        "account" : "zenglingfeng",
        "nickname" : "曾凌峰",
        "id" : 1
    }
}
```

### 账号登录

``/api/v1.0/session``

请求类型  
POST

请求参数

|参数名|类型|必填|描述|  
|-----|----|----|----|  
|account|String|Yes|用户账号|  
|password|String|Yes|用户密码|  

返回示例
```python
{
    "code": 0,
    "data": null,
    "message": "成功登陆",
    "success": true #表示成功登陆，False表示失败，具体信息由message给出
}
```

### 退出登录

``/api/v1.0/session``

请求类型  

DELETE

请求参数

无 

返回示例
```python
{
    "code": 0,
    "data": null,
    "message": "成功,
    "success": true #表示成功退出
}
```
**说明** 如果当前用户未登陆，会返回403

### 更新登录

``/api/v1.0/session``

请求类型  
PUT

### 注册账号

``/api/v1.0/account``

请求类型  
POST

请求参数  

|参数名   |  类型 | 必填 | 描述|
|--------|-------|-----|------|
|account | String| Yes |角色名字|
|password| String|Yes  |密码|
|nickname| String|Yes|昵称|
|sex| int| No|性别:0男 1女 2 保密|
|age| int| No|年龄|
|birth| Date| No|生日|
|tel|String|No|电话|
|country|String|No|国籍|
|province|String|No|省份|
|city|String|No|城市|
|brief_introduction|String|No|自我简介|
|portrait|base64/png格式|No|头像图片|  

返回示例
```python
{
    "code": 0,
    "data": null,
    "message": "成功添加",
    "success": true #表示成功增加，False表示错误，具体信息由message给出
}
```
或，请求数据不完整
```python
{
    "code": 54,
    "data": null,
    "message": "角色名字不能为空",
    "success": False #False表示删错错误
}
```

### 请求账号

请求个人信息

``/api/v1.0/account``

请求类型  
GET

请求参数  

无

返回示例
```python
{
    "message": "成功",
    "code": 0,
    "data": {
        "status": 0,
        "province": "保密",
        "account": "lemon123",
        "tel": "保密",
        "uid": -840729673,
        "city": "保密",
        "country": "中国",
        "age": 18,
        "sex": "保密",
        "brief_introduction": "",
        "birth": null,
        "nickname": "张三123",
        "photo_url": "/data/minitrill/user/photo/default/default.jpg"
    },
    "success": true
}
```






