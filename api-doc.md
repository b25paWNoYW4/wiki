<!-- TITLE: Api Doc -->
<!-- SUBTITLE: A quick summary of Api Doc -->

# 用户管理接口
## 用户列表获取
### 接口地址：/api/admin/user

**请求方式 GET**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 每页条数 |
| name | string | optional | 用户姓名 |
| id | string | optional | 用户ID |
| phone | integer | optional | 用户手机 |

**example**


```json
{
    "status": "success",
    "code": 200,
    "message": {
        "current_page": 1,
        "data": [
            {
                "id": "3b0e8842-ab2f-4e08-9a7a-4aa17cc4de96",
                "name": "王二狗",
                "phone": "15882219670",
                "avatar": "http://video.test/images/user/default.png",
                "gender": 1,
                "type": 0,
                "created_at": "2018-12-25 12:03:35",
                "updated_at": "2018-12-25 13:43:25",
                "role": {
                    "id": 1,
                    "name": "客服",
                    "guard_name": "admin",
                    "created_at": "2018-12-25 10:14:02",
                    "updated_at": "2018-12-25 10:14:02",
                    "pivot": {
                        "model_uuid": "3b0e8842-ab2f-4e08-9a7a-4aa17cc4de96",
                        "role_id": 1,
                        "model_type": "App\\Models\\AdminUser"
                    }
                }
            },
            {
                "id": "51cd8bed-984d-478e-9af0-28fe7d322bdc",
                "name": "Administrator",
                "phone": "18888888888",
                "avatar": "http://video.test/images/user/default.png",
                "gender": 1,
                "type": 1,
                "created_at": "2018-12-07 11:02:15",
                "updated_at": "2018-12-07 11:02:15",
                "role": {
                    "id": 1,
                    "name": "客服",
                    "guard_name": "admin",
                    "created_at": "2018-12-25 10:14:02",
                    "updated_at": "2018-12-25 10:14:02",
                    "pivot": {
                        "model_uuid": "51cd8bed-984d-478e-9af0-28fe7d322bdc",
                        "role_id": 1,
                        "model_type": "App\\Models\\AdminUser"
                    }
                }
            }
        ],
        "first_page_url": "http://video.test/api/admin/user?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://video.test/api/admin/user?page=1",
        "next_page_url": null,
        "path": "http://video.test/api/admin/user",
        "per_page": 15,
        "prev_page_url": null,
        "to": 2,
        "total": 2
    }
}
```

# 系统设置接口
## 系统设置获取

### 地址：/api/admin/setting

**请求方式：GET**

**Parameter: None**

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "AliyunSmsAccessKeyId": "sdfdsfasdf",
            "AliyunSmsAccessKeySecret": "sdfdsfasdf",
            "AliyunVideoAccessKeyId": "sdfdsfasdf",
            "AliyunVideoAccessKeySecret": "sdfdsfasdf",
            "AliyunSmsTemplateSignup": "sdfdsfasdf",
            "AliyunSmsTemplateChangePassword": "sdfdsfasdf",
            "AliyunSmsTemplateForgetPassword": "sdfdsfasdf",
            "AliyunVideoTemplateGroupId": "sdfdsfasdf",
            "UserAgreement": "sdfdsfasdf",
            "MobileBanana": [
                {
                    "image": "http://video.test/a.jpg",
                    "title": "sdf",
                    "content": "sdfasdf"
                },
                {
                    "image": "http://video.test/a.jpg",
                    "title": "sdf",
                    "content": "sdfasdf"
                }
            ]
        }
    }
}
```

**参数注释：**
```text
'AliyunSmsAccessKeyId', // 阿里云子帐号短信 ak
'AliyunSmsAccessKeySecret', // 阿里云子帐号短信 as
'AliyunVideoAccessKeyId', // 阿里云子帐号视频点播 ak
'AliyunVideoAccessKeySecret', // 阿里云子帐号视频点播 as
'AliyunSmsTemplateSignup', // 用户注册短信模板id
'AliyunSmsTemplateChangePassword', // 更改密码短信模板id
'AliyunSmsTemplateForgetPassword', // 找回密码短信模板id
'AliyunVideoTemplateGroupId', // 阿里云视频转码模板id
'UserAgreement', // 用户协议
'MobileBanana' // 轮播图
```

## 系统设置更改

### 地址：/api/admin/setting

**请求方式：POST**


**Parameter: **


| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| AliyunSmsAccessKeyId | string | required | 阿里云子帐号短信AK |
| AliyunSmsAccessKeySecret | string | required | 阿里云子帐号短信AS |
| AliyunVideoAccessKeyId | string | required | 阿里云子帐号视频点播AK |
| AliyunVideoAccessKeySecret | string | required | 阿里云子帐号视频点播AS |
| AliyunSmsTemplateChangePassword | string | required | 更改密码短信模板id |
| AliyunSmsTemplateSignup | string | required | 用户注册短信模板id |
| AliyunSmsTemplateForgetPassword | string | required | 找回密码短信模板id |
| AliyunVideoTemplateGroupId | string | required | 阿里云视频转码模板id |
| UserAgreement | html | required | 用户协议 |
| MobileBanana | array | required | 轮播图 |

*每个轮播图设置项有三个参数，分别为：image, title, content 如下示例*

**Example-Request:**

```json
{"AliyunSmsAccessKeyId":"sdfdsfasdf","AliyunSmsAccessKeySecret":"sdfdsfasdf","AliyunVideoAccessKeyId":"sdfdsfasdf","AliyunVideoAccessKeySecret":"sdfdsfasdf","AliyunSmsTemplateSignup":"sdfdsfasdf","AliyunSmsTemplateChangePassword":"sdfdsfasdf","AliyunSmsTemplateForgetPassword":"sdfdsfasdf","AliyunVideoTemplateGroupId":"sdfdsfasdf","UserAgreement":"sdfdsfasdf","MobileBanana":[{"image":"a.jpg","title":"sdf","content":"sdfasdf"},{"image":"a.jpg","title":"sdf","content":"sdfasdf"}]}
```

**Example-Response:**
```text
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```

