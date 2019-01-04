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

**请求方式：POST**


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

**Parameter: **

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

**Parameter: **

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