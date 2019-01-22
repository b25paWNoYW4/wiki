<!-- TITLE: Mobile -->
<!-- SUBTITLE: A quick summary of Mobile -->

# 基础接口
## 用户注册

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
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```


## 用户登录

### 地址：/api/user/login

**请求方式：POST**


**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| phone | string | required | 手机号 |
| password | string | required | 密码5-32位 |

**Example-Response:待添加**

## 发送短信验证码

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
## 忘记密码

### 地址：/api/user/forget/password

**请求方式：POST**

**需要在请求头内加上Access-token参数，参数值与手机号一致**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| mobile | string | required | 手机号 |
| verifyCode | string | required | 验证码 |
| password | string | required | 密码5-32位 |
| password_confirm | string | required | 重复密码 |

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```
## 退出登录

### 地址：/api/user/logout

**请求方式：POST**


**Parameter:None**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```

## 获取轮播图片及对应文章标题和内容

### 地址：/api/user/banner

**请求方式：GET**


**Parameter:None**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": [
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
```

## 图片上传接口

### 地址：/api/upload/img

**请求方式：POST**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| img | file | required | 图片 |
| editor | int | nullable | 是否editor |

**当传editor参数时，直接返回图片地址，按需使用**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```
# 视频接口
## 视频列表

### 地址：/api/user/video/list

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | string | optional | 数据分页条数 |
| name | string | optional | 视频名称 |
| desc | string | optional | 视频描述 |

*实际返回结果里是有id的*

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "current_page": 1,
            "data": [
                {
                    "name": "doge1",
                    "desc": "视频描述1",
                    "read": 1112
                },
                {
                    "name": "doge1",
                    "desc": "视频描述1",
                    "read": 1112
                }
            ],
            "first_page_url": "http://video.test/api/user/video/list?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/user/video/list?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/user/video/list",
            "per_page": 15,
            "prev_page_url": null,
            "to": 2,
            "total": 2
        }
    }
}
```
## 获取具体视频

### 地址：/api/user/video/{video}

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`video`}` | integer | required | 视频id |

**视频的播放信息在palyAuth里**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "video": {
                "id": 1,
                "name": "doge1",
                "desc": "视频描述1",
                "read": 1113,
                "poster": "http://video.test/sdf1.jpg",
                "order": 12,
                "note": "dsfsdf2",
                "created_at": "2018-12-27 18:01:00",
                "updated_at": "2018-12-27 18:03:18"
            },
            "playAuth": {
                "statusCode": 200,
                "message": {
                    "RequestId": "2ECCA4EB-446D-41F1-9540-B0A31CD478D6",
                    "VideoBase": {
                        "TranscodeMode": "FastTranscode",
                        "CreationTime": "2018-12-13T09:39:00Z",
                        "CoverURL": "http://video.cdfykj.com/4824644c2be94550a5c520a36048765b/snapshots/8409ff79b61942b1a1c8b27fa7d02aca-00003.jpg",
                        "Status": "Normal",
                        "MediaType": "video",
                        "VideoId": "4824644c2be94550a5c520a36048765b",
                        "Duration": "528.886",
                        "OutputType": "cdn",
                        "Title": "莱芜市重要商品追溯体系建设"
                    },
                    "PlayInfoList": {
                        "PlayInfo": [
                            {
                                "Format": "m3u8",
                                "StreamType": "video",
                                "PreprocessStatus": "UnPreprocess",
                                "ModificationTime": "2018-12-13T09:44:27Z",
                                "Height": 540,
                                "PlayURL": "http://video.cdfykj.com/4824644c2be94550a5c520a36048765b/25b7b78519a042e38f771501fcf5ea91-8751e7f9f6e2aeabadbf21a0b62edfd2-ld.m3u8",
                                "CreationTime": "2018-12-13T09:41:49Z",
                                "Status": "Normal",
                                "Duration": "528.9265",
                                "JobId": "14e685f739f84e89b90f7a3a72d755a8",
                                "Encrypt": 0,
                                "Width": 960,
                                "Fps": "25",
                                "Bitrate": "1104.993",
                                "Size": 73057552,
                                "Definition": "LD"
                            },
                            {
                                "Format": "mp4",
                                "StreamType": "video",
                                "PreprocessStatus": "UnPreprocess",
                                "ModificationTime": "2018-12-13T09:43:23Z",
                                "Height": 540,
                                "PlayURL": "http://video.cdfykj.com/4824644c2be94550a5c520a36048765b/25b7b78519a042e38f771501fcf5ea91-7a88bee05944adac7124e9483b53f682-ld.mp4",
                                "CreationTime": "2018-12-13T09:41:49Z",
                                "Status": "Normal",
                                "Duration": "528.9430",
                                "JobId": "1b1542ff2f8a461eb71771cda30101a7",
                                "Encrypt": 0,
                                "Width": 960,
                                "Fps": "25",
                                "Bitrate": "1005.703",
                                "Size": 66494991,
                                "Definition": "LD"
                            }
                        ]
                    }
                }
            }
        }
    }
}
```

# 资讯文章接口
## 资讯文章列表

### 地址：/api/user/article/list

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | string | optional | 数据分页条数 |
| title | string | optional | 文章标题 |

*实际返回结果里是有id的*

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "current_page": 1,
            "data": [
                {
                    "title": "王二狗2",
                    "thumbnail": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
                    "read": 1031
                },
                {
                    "title": "王二狗3",
                    "thumbnail": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
                    "read": 103
                }
            ],
            "first_page_url": "http://video.test/api/user/article/list?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/user/article/list?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/user/article/list",
            "per_page": 15,
            "prev_page_url": null,
            "to": 2,
            "total": 2
        }
    }
}
```
## 获取具体文章

### 地址：/api/user/article/{article}

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`article`}` | integer | required | 文章id |


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "id": 1,
            "title": "王二狗2",
            "subtitle": "我是恩的萨2",
            "thumbnail": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
            "read": 1032,
            "content": "遗产纠纷2",
            "order": 2,
            "note": null,
            "created_at": "2018-12-27 12:11:09",
            "updated_at": "2019-01-03 15:11:49"
        }
    }
}
```

# 律师接口
## 律师列表

### 地址：/api/user/lawyer/list

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | string | optional | 数据分页条数 |
| name | string | optional | 律师姓名 |

*实际返回结果里是有id的*

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "current_page": 1,
            "data": [
                {
                    "name": "王二狗3",
                    "avatar": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg"
                }
            ],
            "first_page_url": "http://video.test/api/user/lawyer/list?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/user/lawyer/list?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/user/lawyer/list",
            "per_page": 15,
            "prev_page_url": null,
            "to": 1,
            "total": 1
        }
    }
}
```
## 获取具体律师接口

### 地址：/api/user/lawyer/{lawyer}

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`lawyer`}` | integer | required | 律师id |


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "id": 1,
            "name": "王二狗3",
            "contact": "15882219670",
            "avatar": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
            "wechat": null,
            "introduction": "secret",
            "order": 1,
            "skill": "遗产纠纷、婚姻纠纷",
            "created_at": "2018-12-27 11:55:41",
            "updated_at": "2018-12-27 11:57:15"
        }
    }
}
```

# 个人中心接口
## 获取用户个人信息

### 地址：/api/user/profile

**请求方式：GET**

**Parameter:None**


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "name": "doge1",
            "phone": "18888888888",
            "avatar": "http://video.test/default1.jpg",
            "verified": true,
            "gender": 1,
            "verified_at": "2018-12-28 18:49:05",
            "created_at": "2018-12-07 11:02:15",
            "updated_at": "2019-01-03 15:17:46"
        }
    }
}
```
## 获取用户历史认证记录

### 地址：/api/user/audit/result

**请求方式：GET**

**Parameter:None**

**示例返回待更新**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": []
    }
}
```

## 更新用户个人信息

### 地址：/api/user/profile

**请求方式：POST**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 用户姓名 |
| password | string | optional | 密码 |
| password_confirm | string | required_if:password | 重复密码 |
| gender | integer | required | 用户性别0女1男 |
| avatar | string | required | 用户头像 |


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```

## 用户重新认证

### 地址：/api/user/re/auth

**请求方式：POST**


**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 用户姓名 |
| company | string | required | 公司名称 |
| address | string | required | 公司地址 |
| certificates | array | required | 公司证书图片 |


**Example-Response:1**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```
**Example-Response:2**

```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 400,
        "message": "已完成认证，无法再次认证"
    }
}
```

## 用户修改手机号

### 地址：/api/user/profile/phoneChange

**请求方式：POST**

**需要在请求头内加上Access-token参数，参数值与手机号一致**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| mobile | string | required | 手机号 |
| verifyCode | string | required | 验证码 |

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```

# 聊天相关
## 获取聊天记录

### 地址：/api/user/message/history

**请求方式：GET**

**Parameter:None**
| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| user_id | string | required | 对应客服的id |
| limit | string | required | 数据分页条数 |

**示例返回结果待更新**

**Example-Response:**
```json
{
    "20181219000001": [
        {
            "id": 1,
            "chat_no": "20181219000001",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsafasdf",
            "created_at": "2018-12-19 17:49:03",
            "updated_at": "2018-12-19 17:49:03",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 2,
            "chat_no": "20181219000001",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsafasdf",
            "created_at": "2018-12-19 17:52:06",
            "updated_at": "2018-12-19 17:52:06",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 3,
            "chat_no": "20181219000001",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsafasdf",
            "created_at": "2018-12-19 17:52:32",
            "updated_at": "2018-12-19 17:52:32",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181219000002": [
        {
            "id": 4,
            "chat_no": "20181219000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsafasdf",
            "created_at": "2018-12-19 18:00:04",
            "updated_at": "2018-12-19 18:00:04",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 5,
            "chat_no": "20181219000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsafasdf",
            "created_at": "2018-12-19 18:04:09",
            "updated_at": "2018-12-19 18:04:09",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 6,
            "chat_no": "20181219000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsafasdf",
            "created_at": "2018-12-19 18:05:42",
            "updated_at": "2018-12-19 18:05:42",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 7,
            "chat_no": "20181219000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf",
            "created_at": "2018-12-19 18:06:20",
            "updated_at": "2018-12-19 18:06:20",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 8,
            "chat_no": "20181219000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf",
            "created_at": "2018-12-19 18:06:31",
            "updated_at": "2018-12-19 18:06:31",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 9,
            "chat_no": "20181219000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:06:55",
            "updated_at": "2018-12-19 18:06:55",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181219000003": [
        {
            "id": 10,
            "chat_no": "20181219000003",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:14:31",
            "updated_at": "2018-12-19 18:14:31",
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181219000004": [
        {
            "id": 11,
            "chat_no": "20181219000004",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:21:30",
            "updated_at": "2018-12-19 18:21:30",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 12,
            "chat_no": "20181219000004",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:21:47",
            "updated_at": "2018-12-19 18:21:47",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 13,
            "chat_no": "20181219000004",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:22:21",
            "updated_at": "2018-12-19 18:22:21",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 14,
            "chat_no": "20181219000004",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:25:26",
            "updated_at": "2018-12-19 18:25:26",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 15,
            "chat_no": "20181219000004",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:25:36",
            "updated_at": "2018-12-19 18:25:36",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 16,
            "chat_no": "20181219000004",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 18:27:21",
            "updated_at": "2018-12-19 18:27:21",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181219000005": [
        {
            "id": 17,
            "chat_no": "20181219000005",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-19 19:01:54",
            "updated_at": "2018-12-19 19:01:54",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181220000001": [
        {
            "id": 18,
            "chat_no": "20181220000001",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:06:44",
            "updated_at": "2018-12-20 10:06:44",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 19,
            "chat_no": "20181220000001",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:07:20",
            "updated_at": "2018-12-20 10:07:20",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 20,
            "chat_no": "20181220000001",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:09:54",
            "updated_at": "2018-12-20 10:09:54",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 21,
            "chat_no": "20181220000001",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:10:56",
            "updated_at": "2018-12-20 10:10:56",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 22,
            "chat_no": "20181220000001",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:11:58",
            "updated_at": "2018-12-20 10:11:58",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 23,
            "chat_no": "20181220000001",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:13:22",
            "updated_at": "2018-12-20 10:13:22",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181220000002": [
        {
            "id": 24,
            "chat_no": "20181220000002",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:15:16",
            "updated_at": "2018-12-20 10:15:16",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 25,
            "chat_no": "20181220000002",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "sdf1",
            "created_at": "2018-12-20 10:15:52",
            "updated_at": "2018-12-20 10:15:52",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 26,
            "chat_no": "20181220000002",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsfasdf",
            "created_at": "2018-12-20 10:16:45",
            "updated_at": "2018-12-20 10:16:45",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ],
    "20181220000003": [
        {
            "id": 27,
            "chat_no": "20181220000003",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "dsfasdf",
            "created_at": "2018-12-20 10:21:52",
            "updated_at": "2018-12-20 10:21:52",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 28,
            "chat_no": "20181220000003",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "NIHAO",
            "created_at": "2018-12-20 10:22:12",
            "updated_at": "2018-12-20 10:22:12",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 29,
            "chat_no": "20181220000003",
            "admin_user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "type": 0,
            "message_type": 0,
            "content": "FSGDASDG",
            "created_at": "2018-12-20 10:23:06",
            "updated_at": "2018-12-20 10:23:06",
            "admin_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ]
}
```
## 获取客服列表

### 地址：/api/user/message/customerService/list

**请求方式：GET**

**Parameter:None**

**示例返回待更新**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": [
        {
            "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "name": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "avatar": "http://video.test/images/user/default.png",
            "online_state": true
        }
    ]
}
```

## 获取未读消息列表

### 地址：/api/user/message/unread/list

**请求方式：GET**

**Parameter:None**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": [
        {
            "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "name": "doge",
            "value": 6
        }
    ]
}
```
## 获取具体未读消息

### 地址：/api/user/message/unread

**请求方式：GET**

**Parameter:None**
| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| user_id | string | required | 对应客服的id |

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": [
        {
            "id": 31,
            "chat_no": "20181220000005",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 0,
            "message_type": 0,
            "content": "test124",
            "created_at": "2018-12-20 14:02:03",
            "updated_at": "2018-12-24 13:46:14",
            "state": 0,
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 34,
            "chat_no": "20181220000006",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 0,
            "message_type": 0,
            "content": "test124",
            "created_at": "2018-12-20 14:09:28",
            "updated_at": "2018-12-24 13:46:14",
            "state": 0,
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 36,
            "chat_no": "20181220000006",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 0,
            "message_type": 0,
            "content": "test124324",
            "created_at": "2018-12-20 14:09:43",
            "updated_at": "2018-12-24 13:46:14",
            "state": 0,
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 38,
            "chat_no": "20181220000006",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 0,
            "message_type": 0,
            "content": "test124324424",
            "created_at": "2018-12-20 14:09:57",
            "updated_at": "2018-12-24 13:46:14",
            "state": 0,
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 39,
            "chat_no": "20181220000007",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 0,
            "message_type": 0,
            "content": "聊天内容",
            "created_at": "2018-12-20 16:38:28",
            "updated_at": "2018-12-24 13:46:14",
            "state": 0,
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 40,
            "chat_no": "20181224000001",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 0,
            "message_type": 0,
            "content": "聊天内容",
            "created_at": "2018-12-24 13:37:56",
            "updated_at": "2018-12-24 13:46:14",
            "state": 0,
            "admin_user": {
                "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "name": "doge",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ]
}
```
## 更新具体消息阅读状态

### 地址：/api/user/message/finishRead

**请求方式：POST**

**Parameter:**
| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| user_id | string | required | 客服的id |

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "操作成功"
    }
}
```
## 发送消息

### 地址：/api/user/message/send

**请求方式：POST**

**请求头一定要带X-Socket-Id 参数，Vue Axios 以外框架可以手动获取**

```js
var socketId = Echo.socketId();
```

**Parameter:None**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| to_user | string | required | 对应客服的id |
| content | string | required | 聊天内容 |

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "message": "20181220000007"
}
```