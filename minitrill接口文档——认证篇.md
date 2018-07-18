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
|54  |请求有误        |
待补充

## 接口详情

### 检查登录

``/api/v1.0/auth/check``

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
        "username" : "xuzeshan",
        "realname" : "许泽珊",
        "id" : 1
    }
}
```