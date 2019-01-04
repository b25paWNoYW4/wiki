<!-- TITLE: Mobile -->
<!-- SUBTITLE: A quick summary of Mobile -->

# 用户相关接口
## 注册接口

### 地址：/api/user/signUp

**请求方式：POST**

**需要在请求头内加上Access-token参数，参数值与手机号一致**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| mobile | string | required | 手机号 |
| verifyCode | string | required | 验证码 |
| password | string | required | 密码5-32位 |
| name | string | required | 联系人姓名 |
| company | string | required | 公司名称 |
| address | string | required | 公司地址 |
| certificates | array | required | 证件图片，注意是array |

**Example-Response:**
```json
{
    "status": "success",
    "code": 400,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```

## 短信验证码接口

### 地址：/api/verifyCode

**请求方式：POST**

**需要在请求头内加上Access-token参数，参数值与手机号一致**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| mobile | string | required | 手机号 |
| type | string | required | 验证码类型 |

```text
可选验证码类型列表：
['signUp', 'changePassword', 'forgetPassword']
分别对应：注册，改手机号，忘记密码
```


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "success": true,
            "type": "sms_sent_success",
            "message": "短信验证码发送成功，请注意查收"
        }
    }
}
```
