# 一、用户登录
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




