[toc]
# user module
## 1.1 登录
POST
/api/user/login
```json
{
  "userName": "string",
  "password": "string"
}
```
响应:
普通用户成功0，管理员成功1，失败-1
```json
{
  "code": 0,
  "error_msg": "string",
  "data": {
  }
}
```
### 1.2 注册
请求：(POST)
/api/user/register
```json
{
  "username": "string",
  "password": "string"
}
```
响应：
成功0，失败-1
```json
{
  "code": 0,
  "error_msg": "string",
  "data": {
    "username": "string"
  }
}
```

## 1.3 修改信息
**request**：
（Post）
/api/user/modify
（params形式）
```json
{
  "old_password": "string",
  "new_password": "string",
  "old_username": "string",
  "new_username": "string"
}
```


**response**：
0成功 1失败
```json
{
  "code": 0,
  "error_msg": "string",
  "data": {
  }
}
```


# Post module
## 2.1 发帖
**request**
(Post)
/api/post
body中的form-data形式（看群里的图）
1. file：image或video
2. post： application/json type

post json格式
```json
{
  "content_type": 1,
  "text": "string",
  "title":"string",
  "ownername":"string"
  "location_x": 0,
  "location_y": 0
}
```
**response**
```json
{
  "code": 0,
  "error_msg": "string",
  "data": {
    "id": "1",
    "title": "string",
    "content_type": "0(text only), 1(image or video)",
    "text": "This is a new text",
    "media_url": "http://aaa",
    "location_x": 123.1,
    "location_y": 123.2
  }
}
```

## 2.2 删帖
**request**
（post）
/api/post/delete
param类型
```json
{
	"post_id":"string"
}
```
**response**
0成功 1失败
```json
{
  "code": 0,
  "error_msg": "string",
  "data": {
  }
}
```



## 2.3 显示某个post具体内容
（get）
/api/post
param类型
```json
{
	"post_id":"string"
}
```

**response**
```json
{
    "code": 0,
    "error_msg": "",
    "data": {
        "content_type": 1,
        "location_x": 0.0,
        "location_y": 0.0,
        "id": "ksl_20230514200258",
        "text": "string",
        "title": "ksls post",
        "media_url": "http://192.168.0.124:9001/2023051420047.png"
    }
}
```
前端通过图片media_url打开图片

## 2.4 帖子列表
**request**
(get)
/api/post
param形式
```json
{
	"page_num":int, //从1开始数
	"page_size":int,
	"location_x":float,
	"location _y":float,
	"distance":float
}
```
**response**
```json
{
    "code": 0,
    "error_msg": "",
    "data": {
        "posts": [
            {
                "id": "anonymous_20230515121749",
                "title": "no title",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "anonymous",
                "post_time": "2023-05-15 12:17"
            },
            {
                "id": "anonymous_20230515121803",
                "title": "no title",
                "content_type": 1,
                "text": "string",
                "media_url": "http://192.168.0.124:90017.png",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "anonymous",
                "post_time": "2023-05-15 12:18"
            },
            {
                "id": "ksl_20230514200258",
                "title": "ksls post",
                "content_type": 1,
                "text": "string",
                "media_url": "http://192.168.0.124:9001/2747.png",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "ksl",
                "post_time": "2023-05-14 20:02"
            }
        ]
    }
}
```
posts 直接把post信息全贴上去了。。。写起来方便

## 2.5 我发表的帖子
**request**
(get)
/api/post/mypost
param形式
```json
{
	"page_num":0, //从1开始数
	"page_size":3,
	"username":"ksl"
}
```
**response**
```json
{
    "code": 0,
    "error_msg": "",
    "data": {
        "posts": [
            {
                "id": "anonymous_20230515121749",
                "title": "no title",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "ksl",
                "post_time": "2023-05-15 12:17"
            },
            {
                "id": "anonymous_20230515121803",
                "title": "no title",
                "content_type": 1,
                "text": "string",
                "media_url": "http://192.168.0.124:90017.png",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "ksl",
                "post_time": "2023-05-15 12:18"
            },
            {
                "id": "ksl_20230514200258",
                "title": "ksls post",
                "content_type": 1,
                "text": "string",
                "media_url": "http://192.168.0.124:9001/2747.png",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "ksl",
                "post_time": "2023-05-14 20:02"
            }
        ]
    }
}
```

## 2.6 更贴
**request**
(Put)
/api/post
body中的form-data形式（看群里的图）
1. post： application/json type
   {
	   "title":"string",
	   "text":"string"
   }
2. post_id:普通类型


**response**
   ```json
   {
    "code": 0,
    "error_msg": "",
    "data": {
        "posts": [
            {
                "id": "anonymous_20230515121749",
                "title": "no title",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "location_x": 0.0,
                "location_y": 0.0,
                "ownername": "ksl",
                "post_time": "2023-05-15 12:17"
            }]
	}
```

# Comment module
## 3.1 发评论
**request**
(Post)
/api/comment
body中的form-data形式（看群里的图）
1. file：image或video
2. comment： application/json type
  
comment json格式
```json
{
  "post_id": "string",
  "content_type": 1,
  "text": "string"
  "ownername":"string"
}
```

**response**
```json
{
    "code": 0,
    "error_msg": "",
    "data": {
        "id": "anonymous users_20230515162432",
        "text": "string",
        "content_type": 1,
        "media_url": "http://192.168.0.124:9001/20230515167.png",
        "ownername": "anonymous users"
    }
}
````

## 3.2 删评
**request**
(Post)
/api/comment/delete
param类型
```json
{
	"comment_id":"string"
}
```

**response**
0成功 1失败
```json
{
  "code": 0,
  "error_msg": "string",
  "data": {
  }
}
```

## 3.3 获得评论list
**request**
(get)
/api/comment
param形式
```json
{
	"page_num":int, //从1开始数
	"page_size":int,
	"post_id":"string"  //什么帖子下的评论
}
```

**response**
```json
{
    "code": 0,
    "error_msg": "",
    "data": {
        "comments": [
            {
                "id": "anonymous users_20230515161747",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "ownername": "anonymous users",
                "post_id": "ksl_20230514200258"
            },
            {
                "id": "anonymous users_20230515162008",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "ownername": "anonymous users",
                "post_id": "ksl_20230514200258"
            },
            {
                "id": "anonymous users_20230515162104",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "ownername": "anonymous users",
                "post_id": "ksl_20230514200258"
            }
        ]
    }
}
```
comments 直接把comment全部信息全贴上去了。。。写起来方便

## 3.4 我的评论
**request**
(get)
/api/comment/mycomment
param形式
```json
{
	"page_num":0, //从1开始数
	"page_size":3,
	"username":"string"  //什么帖子下的评论
}
```

**response**
```json
{
    "code": 0,
    "error_msg": "",
    "data": {
        "comments": [
            {
                "id": "anonymous users_20230515161747",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "ownername": "string",
                "post_id": "ksl_20230514200258"
            },
            {
                "id": "anonymous users_20230515162008",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "ownername": "string",
                "post_id": "ksl_20230514200258"
            },
            {
                "id": "anonymous users_20230515162104",
                "content_type": 0,
                "text": "string",
                "media_url": "",
                "ownername": "string",
                "post_id": "ksl_20230514200258"
            }
        ]
    }
}
```


# 实体类schemas
## 1 User
```java
public class User {
    String userId;
     @JsonAlias(value = {"username","userName"}) //别用名字的意思
    String username;
    String password;
    @JsonAlias(value = {"is_manager"})
    boolean ismanager;
	
	//下面方法函数省略
```

## 2 Post
```java
public class Post {
    @JsonAlias(value = {"id","post_id"})  //别用名字的意思
    String id;
    String title;
    int content_type;
    String text;
    String media_url;
    float location_x;
    float location_y;
    String ownername;
    String post_time;
	
	//下面方法函数省略
```
## 3 Comment
```java
public class Comment {
    @JsonAlias(value = {"id","comment_id"})
    String id;
    int content_type;
    String text;
    String media_url;
    String ownername;
    String post_id;
	
	//下面方法函数省略
}
```