<!-- TITLE: PC 后台接口文档-2 -->
<!-- SUBTITLE: A quick summary of Api Doc -->

# 聊天记录管理接口
## ~~消息列表获取~~

### 地址：/api/admin/message

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 分页数据数 |
| content | string | optional | 聊天内容 |

```text

参数解释：
chat_no:会话编号
type => 0 系统客服发送给用户的消息
type => 1 用户发送给客服的消息
state => 消息接收者的已读未读状态，0未读1已读

```

**Example-Response:None**


## 聊天记录客服列表

### 地址：/api/admin/message/mainList

**请求方式：GET**

**Parameter:None**

```text

参数解释：
messageCount:消息总条数
customer => 客服id
customer_info => 客服信息

```

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": [
            {
                "messageCount": 21,
                "customer": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "customer_info": {
                    "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "name": "doge1",
                    "avatar": "http://video.test/default1.jpg",
                    "created_at": "2018-12-07 11:02:15",
                    "updated_at": "2019-01-04 13:47:13"
                }
            },
            {
                "messageCount": 19,
                "customer": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "customer_info": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "必填王鹅肉",
                    "avatar": "http://video.test/images/user/default.png",
                    "created_at": "2018-12-19 17:46:55",
                    "updated_at": "2018-12-29 17:53:30"
                }
            }
        ]
    }
}
```


## 客服历史聊天对象列表

### 地址：/api/admin/message/{customer}/list

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`customer`}` | string | required | 客服id |

```text

参数解释：
messageCount:消息总条数
mobileUser => 用户id
mobileUser_info => 用户信息

```

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": [
            {
                "messageCount": 9,
                "mobileUser": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "mobileUser_info": {
                    "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "name": "doge1",
                    "phone": "13118811351",
                    "avatar": "http://video.test/default1.jpg",
                    "verified": 1,
                    "gender": 1,
                    "verified_at": "2018-12-28 18:49:05",
                    "created_at": "2018-12-07 11:02:15",
                    "updated_at": "2019-01-04 13:47:13"
                }
            },
            {
                "messageCount": 12,
                "mobileUser": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "mobileUser_info": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "必填王鹅肉",
                    "phone": "18888888880",
                    "avatar": "http://video.test/images/user/default.png",
                    "verified": 1,
                    "gender": 1,
                    "verified_at": "2018-12-29 00:00:00",
                    "created_at": "2018-12-19 17:46:55",
                    "updated_at": "2018-12-29 17:53:30"
                }
            }
        ]
    }
}
```

## 客服用户消息记录列表

### 地址：/api/admin/message/{customer}/{user}/history

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`customer`}` | string | required | 客服id |
| `{`user`}` | string | required | 用户id |
| limit | integer | optional | 数据分页条数 |

```text

参数解释：
chat_no:会话编号
type => 0 系统客服发送给用户的消息
type => 1 用户发送给客服的消息
state => 消息接收者的已读未读状态，0未读1已读

```

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
                    "id": 41,
                    "chat_no": "20181224000002",
                    "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "type": 1,
                    "message_type": 0,
                    "content": "聊天内容",
                    "created_at": "2018-12-24 15:12:28",
                    "updated_at": "2018-12-24 15:43:04",
                    "state": 1,
                    "admin_user": {
                        "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
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
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
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
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
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
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
                {
                    "id": 37,
                    "chat_no": "20181220000005",
                    "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "type": 1,
                    "message_type": 0,
                    "content": "FSGDASDGsdf1234242",
                    "created_at": "2018-12-20 14:09:54",
                    "updated_at": "2018-12-24 15:43:04",
                    "state": 1,
                    "admin_user": {
                        "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
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
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
                {
                    "id": 35,
                    "chat_no": "20181220000005",
                    "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "type": 1,
                    "message_type": 0,
                    "content": "FSGDASDGsdf123",
                    "created_at": "2018-12-20 14:09:38",
                    "updated_at": "2018-12-24 15:43:04",
                    "state": 1,
                    "admin_user": {
                        "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
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
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
                {
                    "id": 33,
                    "chat_no": "20181220000005",
                    "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "type": 1,
                    "message_type": 0,
                    "content": "FSGDASDGsdf",
                    "created_at": "2018-12-20 14:09:18",
                    "updated_at": "2018-12-24 15:43:04",
                    "state": 1,
                    "admin_user": {
                        "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
                {
                    "id": 32,
                    "chat_no": "20181220000004",
                    "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "type": 1,
                    "message_type": 0,
                    "content": "FSGDASDGsdf",
                    "created_at": "2018-12-20 14:02:15",
                    "updated_at": "2018-12-24 15:43:04",
                    "state": 1,
                    "admin_user": {
                        "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
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
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
                {
                    "id": 30,
                    "chat_no": "20181220000004",
                    "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "type": 1,
                    "message_type": 0,
                    "content": "FSGDASDG",
                    "created_at": "2018-12-20 13:58:03",
                    "updated_at": "2018-12-24 15:43:04",
                    "state": 1,
                    "admin_user": {
                        "id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                        "name": "doge1",
                        "avatar": "http://video.test/default1.jpg"
                    },
                    "mobile_user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉",
                        "phone": "18888888880",
                        "avatar": "http://video.test/images/user/default.png",
                        "verified": 1,
                        "gender": 1,
                        "type": 0,
                        "verified_at": "2018-12-29 00:00:00",
                        "created_at": "2018-12-19 17:46:55",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                }
            ],
            "first_page_url": "http://video.test/api/admin/message/b6affc3a-27ff-4073-ab0c-d6fefa57aad6/ce8a75d0-47b3-4cee-bdaf-a254b76d0764/history?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/admin/message/b6affc3a-27ff-4073-ab0c-d6fefa57aad6/ce8a75d0-47b3-4cee-bdaf-a254b76d0764/history?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/admin/message/b6affc3a-27ff-4073-ab0c-d6fefa57aad6/ce8a75d0-47b3-4cee-bdaf-a254b76d0764/history",
            "per_page": 15,
            "prev_page_url": null,
            "to": 12,
            "total": 12
        }
    }
}
```

## 客服用户消息记录一键删除

### 地址：/api/admin/message/{customer}/{user}/history

**请求方式：DELETE**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`customer`}` | string | required | 客服id |
| `{`user`}` | string | required | 用户id |


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

## ~~消息记录删除~~

### 地址：/api/admin/message/{message}

**请求方式：DELETE**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`message`}` | integer | required | 记录id |

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
# 客服聊天接口
## 未读消息获取

### 地址：/api/admin/message/unread/list

**请求方式：GET**

**Parameter:None**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": [
        {
            "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "name": "test",
            "value": 6
        }
    ]
}
```

## 发送消息

### 地址：/api/admin/message/send

**请求方式：POST**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| to_user | string | required | app用户的id |
| content | string | required | 消息内容 |

*返回的是当前会话编号，暂时还用不到，不用管*

**Example-Response:**

```json

{
    "status": "success",
    "code": 200,
    "message": "20181224000002"
}

```
## 获取具体未读消息

### 地址：/api/admin/message/unread

**请求方式：GET**

**Parameter:**
| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| user_id | string | required | app用户的id |
**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": [
        {
            "id": 30,
            "chat_no": "20181220000004",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 1,
            "message_type": 0,
            "content": "FSGDASDG",
            "created_at": "2018-12-20 13:58:03",
            "updated_at": "2018-12-20 13:58:03",
            "state": 0,
            "mobile_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 32,
            "chat_no": "20181220000004",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 1,
            "message_type": 0,
            "content": "FSGDASDGsdf",
            "created_at": "2018-12-20 14:02:15",
            "updated_at": "2018-12-20 14:02:15",
            "state": 0,
            "mobile_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 33,
            "chat_no": "20181220000005",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 1,
            "message_type": 0,
            "content": "FSGDASDGsdf",
            "created_at": "2018-12-20 14:09:18",
            "updated_at": "2018-12-20 14:09:18",
            "state": 0,
            "mobile_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 35,
            "chat_no": "20181220000005",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 1,
            "message_type": 0,
            "content": "FSGDASDGsdf123",
            "created_at": "2018-12-20 14:09:38",
            "updated_at": "2018-12-20 14:09:38",
            "state": 0,
            "mobile_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 37,
            "chat_no": "20181220000005",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 1,
            "message_type": 0,
            "content": "FSGDASDGsdf1234242",
            "created_at": "2018-12-20 14:09:54",
            "updated_at": "2018-12-20 14:09:54",
            "state": 0,
            "mobile_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        },
        {
            "id": 41,
            "chat_no": "20181224000002",
            "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
            "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
            "type": 1,
            "message_type": 0,
            "content": "聊天内容",
            "created_at": "2018-12-24 15:12:28",
            "updated_at": "2018-12-24 15:12:28",
            "state": 0,
            "mobile_user": {
                "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "name": "test",
                "avatar": "http://video.test/images/user/default.png"
            }
        }
    ]
}
```
## 获取和某一app用户的历史消息

### 地址：/api/admin/message/history

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| user_id | string | required | app用户的id |

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "message": {
        "current_page": 1,
        "data": [
            {
                "id": 30,
                "chat_no": "20181220000004",
                "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "type": 1,
                "message_type": 0,
                "content": "FSGDASDG",
                "created_at": "2018-12-20 13:58:03",
                "updated_at": "2018-12-24 15:43:04",
                "state": 1,
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            },
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
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            },
            {
                "id": 32,
                "chat_no": "20181220000004",
                "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "type": 1,
                "message_type": 0,
                "content": "FSGDASDGsdf",
                "created_at": "2018-12-20 14:02:15",
                "updated_at": "2018-12-24 15:43:04",
                "state": 1,
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            },
            {
                "id": 33,
                "chat_no": "20181220000005",
                "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "type": 1,
                "message_type": 0,
                "content": "FSGDASDGsdf",
                "created_at": "2018-12-20 14:09:18",
                "updated_at": "2018-12-24 15:43:04",
                "state": 1,
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
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
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            },
            {
                "id": 35,
                "chat_no": "20181220000005",
                "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "type": 1,
                "message_type": 0,
                "content": "FSGDASDGsdf123",
                "created_at": "2018-12-20 14:09:38",
                "updated_at": "2018-12-24 15:43:04",
                "state": 1,
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
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
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            },
            {
                "id": 37,
                "chat_no": "20181220000005",
                "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "type": 1,
                "message_type": 0,
                "content": "FSGDASDGsdf1234242",
                "created_at": "2018-12-20 14:09:54",
                "updated_at": "2018-12-24 15:43:04",
                "state": 1,
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
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
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
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
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
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
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            },
            {
                "id": 41,
                "chat_no": "20181224000002",
                "admin_user_id": "b6affc3a-27ff-4073-ab0c-d6fefa57aad6",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "type": 1,
                "message_type": 0,
                "content": "聊天内容",
                "created_at": "2018-12-24 15:12:28",
                "updated_at": "2018-12-24 15:43:04",
                "state": 1,
                "mobile_user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test",
                    "avatar": "http://video.test/images/user/default.png"
                }
            }
        ],
        "first_page_url": "http://video.test/api/admin/message/history?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://video.test/api/admin/message/history?page=1",
        "next_page_url": null,
        "path": "http://video.test/api/admin/message/history",
        "per_page": 15,
        "prev_page_url": null,
        "to": 12,
        "total": 12
    }
}
```
# 律师接口
## 律师信息创建

### 地址：/api/admin/lawyer

**请求方式：POST**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 律师姓名 |
| contact | integer | required | 律师联系方式（手机） |
| avatar | string | required | 律师头像 |
| introduction | html | optional | 律师介绍 |
| wechat | string | optional | 律师微信号 |
| skill | string | optional | 律师擅长技能 |


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

## 律师信息列表

### 地址：/api/admin/lawyer

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | optional | 律师姓名 |
| id | integer | optional | 律师id |
| limit | integer | optional | 分页数据数 |


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": {
        "current_page": 1,
        "data": [
            {
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
            },
            {
                "id": 2,
                "name": "王二狗4",
                "contact": "15882219671",
                "avatar": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
                "wechat": null,
                "introduction": "撒地方",
                "order": 2,
                "skill": "吹水",
                "created_at": "2018-12-27 11:59:15",
                "updated_at": "2018-12-27 11:59:15"
            }
        ],
        "first_page_url": "http://video.test/api/admin/lawyer?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://video.test/api/admin/lawyer?page=1",
        "next_page_url": null,
        "path": "http://video.test/api/admin/lawyer",
        "per_page": 15,
        "prev_page_url": null,
        "to": 2,
        "total": 2
    }
}
```
## 律师信息修改

### 地址：/api/admin/lawyer/{lawyer}

**请求方式：PATCH**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`lawyer`}` | integer | required | 律师id |
| name | string | required | 律师姓名 |
| contact | integer | required | 律师联系方式（手机） |
| avatar | string | required | 律师头像 |
| introduction | html | optional | 律师介绍 |
| wechat | string | optional | 律师微信号 |
| skill | string | optional | 律师擅长技能 |

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
## 律师信息删除
### 接口地址：/api/admin/lawyer/{lawyer}

**请求方式 DELETE**

**Parameter：**

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
        "message": "操作成功"
    }
}
```

## 律师浏览记录获取

### 地址：/api/admin/lawyer/view/record

**请求方式：GET**

**Parameter**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 分页数据条数 |
| name | string | optional | 律师姓名 |
| use_name | string | optional | 用户姓名 |


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
                    "id": 1,
                    "lawyer_id": 1,
                    "name": "123",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "user_name": "123",
                    "view_at": "2018-12-27 14:39:18",
                    "lawyer": {
                        "id": 1,
                        "name": "王二狗3"
                    },
                    "user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉"
                    }
                }
            ],
            "first_page_url": "http://video.test/api/admin/lawyer/view/record?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/admin/lawyer/view/record?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/admin/lawyer/view/record",
            "per_page": "15",
            "prev_page_url": null,
            "to": 1,
            "total": 1
        }
    }
}
```
# 视频管理接口

## 获取视频上传凭证

### 地址：/api/admin/video/uploadAuth

**请求方式：POST**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| title | string | required | 视频名称 |
| desc | string | optional | 视频描述 |
| file | string | required | 文件名，一定要包含扩展名 |
| poster | url | optional | 视频封面图片，图片url |
| tags | string | optional | 视频的标签，多个用逗号分隔 |


**支持的视频格式列表：**
```text
['avi','wmv','mpeg','mp4','mov','mkv','flv','f4v','m4v','rmvb','rm','3gp','dat','ts','mts','vob']
```

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "UploadAddress": "eyJFbmRwb2ludCI6Imh0dHBzOi8vb3NzLWNuLXNoYW5naGFpLmFsaXl1bmNzLmNvbSIsIkJ1Y2tldCI6Im91dGluLWEzZGJhYzNiZWQ0YzExZThhNGFmMDAxNjNlMWM5MWM4IiwiRmlsZU5hbWUiOiJjdXN0b21lclRyYW5zL2UyOTdjOTJkYmYyMzAzYzg4YjhhNjkzMjM1OTMzMTg0LzMwNGM1NC0xNjgxN2EyOTY1OS0wMDA1LTVkZGUtYzExLTUzYTUwLmF2aSJ9",
            "VideoId": "86c761ac335d44fea1dd9347c237fbd6",
            "RequestId": "D20C42D3-D088-4A75-B598-24D6DE9439AF",
            "UploadAuth": "eyJTZWN1cml0eVRva2VuIjoiQ0FJUzJ3UjFxNkZ0NUIyeWZTaklyNG5DSEluRXU1Z1o1STZOUVJEM3BtSnRic2w4M3FiTXNEejJJSGxQZTNGaEFPb2V2L2svbVc5VTdmb2NsclVxRnNZZEdCeWFOSnN2dHNzUHFWajdKcGZadjh1ODRZQURpNUNqUWFBcGc4Z1NtWjI4V2Y3d2FmK0FVQXJHQ1RtZDVNZ1lvOWJUY1RHbFFDWnVXLy90b0pWN2I5TVJjeENsWkQ1ZGZybC9MUmRqcjhsbzF4R3pVUEcyS1V6U24zYjNCa2hsc1JZZTcyUms4dmFIeGRhQXpSRGNnVmJtcUpjU3ZKK2pDNEM4WXM5Z0c1MTlYdHlwdm9weGJiR1Q4Q05aNXo5QTlxcDlrTTQ5L2l6YzdQNlFIMzViNFJpTkw4L1o3dFFOWHdoaWZmb2JIYTlZcmZIZ21OaGx2dkRTajQzdDF5dFZPZVpjWDBha1E1dTdrdTdaSFArb0x0OGphWXZqUDNQRTNyTHBNWUx1NFQ0OFpYVVNPRHREWWNaRFVIaHJFazRSVWpYZEk2T2Y4VXJXU1FDN1dzcjIxN290ZzdGeXlrM3M4TWFIQWtXTFg3U0IyRHdFQjRjNGFFb2tWVzRSeG5lelc2VUJhUkJwYmxkN0JxNmNWNWxPZEJSWm9LK0t6UXJKVFg5RXoycExtdUQ2ZS9MT3M3b0RWSjM3V1p0S3l1aDRZNDlkNFU4clZFalBRcWl5a1QwY0ZncGZUSzFSemJQbU5MS205YmFCMjUvelcrUGREZTBkc1Znb1hWTDdwaUdXRzNSTE5uK3p0Sjl4YmtlRStzS1V4ZmZBK1pwclN3RWo2b3hVVkZpSUlkOHhwbEkrdS9Mc3RCbksrNzY2V1NEdDlYY2o1dDdkOHBOejgwSmlaYkRtb1pmTDRHNlA3U1ROTy9aanc1K1BCak0wZTNudEpTd2xtc0wxcjJrY3VoVU1uMXV6UHhzaThGbUwzUTZ5QnBaQ2lhUFRseW9lV3ZZT3libUhGMno4b0g4Y0lOYUk4cXNOWitSdVIrbEhTYzJneGp0dXd2RDNNTDBPQ0Q0M1dYd2FnQUZtZzE0Ym9PaHRYR0JzdmxXSFZoTUZnd0trRlJ2aGppY0tHa3VRV0ZDb3M1MDBXajMxSjFmK1FON1RGbDFIZkhtL0toRkhpUmxZYTRVcVpYK1R5WTg5bXd6c0V1TTViK1gzWkpNKzlvcmRtb2x0NU90MHNrNUNMUWtCM0VFbzhsS0pJV2p5SWZUQmFJcWFBMWs4U01qcThXVGRldGtxUEJvZVcwb2VLTjVyY0E9PSIsIkFjY2Vzc0tleUlkIjoiU1RTLk5Kd1czcFZHOFNMZkM2RkJiOGJGUDFjZ1IiLCJFeHBpcmVVVENUaW1lIjoiMjAxOS0wMS0wNFQwNzo1MTowOFoiLCJBY2Nlc3NLZXlTZWNyZXQiOiJBcmkycG1qVFBHdnlHYUNmRjROTjRFa2V6Unc2RUFiRXVNRE5oYnU3bXJxSyIsIkV4cGlyYXRpb24iOiIzNTExIiwiUmVnaW9uIjoiY24tc2hhbmdoYWkifQ=="
        }
    }
}
```

## 视频信息创建

### 地址：/api/admin/video

**请求方式：POST**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 视频名称 |
| desc | string | required | 视频描述 |
| read | integer | required | 浏览量 |
| videoId | string | required | 视频videoId |
| poster | string | optional | 视频封面 |


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

## 视频信息列表

### 地址：/api/admin/video

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | optional | 视频名 |
| id | integer | optional | 视频id |
| limit | integer | optional | 分页数据数 |


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
                    "id": 1,
                    "name": "doge1",
                    "desc": "视频描述1",
                    "read": 1112,
                    "videoId": "lsdflksdjfljsadlkfjaslkdjf1",
                    "poster": "http://video.test/sdf1.jpg",
                    "order": 12,
                    "note": "dsfsdf2",
                    "created_at": "2018-12-27 18:01:00",
                    "updated_at": "2018-12-27 18:03:18"
                },
                {
                    "id": 2,
                    "name": "doge1",
                    "desc": "视频描述1",
                    "read": 1112,
                    "videoId": null,
                    "poster": "http://video.test/sdf1.jpg",
                    "order": 12,
                    "note": "dsfsdf2",
                    "created_at": "2018-12-27 17:57:14",
                    "updated_at": "2018-12-27 18:00:46"
                },
                {
                    "id": 3,
                    "name": "doge1",
                    "desc": "视频描述1",
                    "read": 1112,
                    "videoId": null,
                    "poster": "http://video.test/sdf1.jpg",
                    "order": 12,
                    "note": "dsfsdf2",
                    "created_at": "2018-12-27 18:01:16",
                    "updated_at": "2018-12-27 18:01:16"
                }
            ],
            "first_page_url": "http://video.test/api/admin/video?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/admin/video?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/admin/video",
            "per_page": 15,
            "prev_page_url": null,
            "to": 3,
            "total": 3
        }
    }
}
```
## 视频信息修改

### 地址：/api/admin/video/{video}

**请求方式：PATCH**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`video`}` | integer | required | 视频id |
| name | string | required | 视频名称 |
| desc | string | required | 视频描述 |
| read | integer | required | 浏览量 |
| videoId | string | required | 视频videoId |
| poster | string | optional | 视频封面 |

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
## 视频信息删除
### 接口地址：/api/admin/video/{video}

**请求方式 DELETE**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`video`}` | integer | required | 视频id |

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

## 视频浏览记录获取

### 地址：/api/admin/video/view/record

**请求方式：GET**

**Parameter**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 分页数据条数 |
| name | string | optional | 视频名 |
| use_name | string | optional | 用户姓名 |


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
                    "id": 1,
                    "video_id": 1,
                    "name": "三大",
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "user_name": "123",
                    "view_at": "2018-12-27 17:23:37",
                    "video": {
                        "id": 1,
                        "name": "doge1",
                        "desc": "视频描述1"
                    },
                    "user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉"
                    }
                }
            ],
            "first_page_url": "http://video.test/api/admin/video/view/record?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/admin/video/view/record?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/admin/video/view/record",
            "per_page": "15",
            "prev_page_url": null,
            "to": 1,
            "total": 1
        }
    }
}
```
# 文章资讯接口
## 文章资讯创建

### 地址：/api/admin/article

**请求方式：POST**

**Parameter**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| title | string | required | 文章标题 |
| thumbnail | string | required |文章封面图 |
| read | integer | required | 文章浏览量 |
| content | html | optional | 文章内容 |


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
## 文章资讯列表

### 地址：/api/admin/article

**请求方式：GET**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| title | string | optional | 文章标题 |
| id | integer | optional | 文章id |
| limit | integer | optional | 分页数据数 |


**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "message": {
        "current_page": 1,
        "data": [
            {
                "id": 1,
                "title": "王二狗1",
                "subtitle": "我是恩的萨1",
                "type": 0,
                "thumbnail": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
                "read": 1031,
                "content": "遗产纠纷1",
                "order": 1,
                "index_display": 0,
                "note": null,
                "created_at": "2018-12-27 12:11:09",
                "updated_at": "2018-12-27 12:12:17"
            },
            {
                "id": 2,
                "title": "王二狗3",
                "subtitle": "我是恩的萨3",
                "type": 0,
                "thumbnail": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
                "read": 103,
                "content": "遗产纠纷",
                "order": 0,
                "index_display": 0,
                "note": null,
                "created_at": "2018-12-27 12:11:47",
                "updated_at": "2018-12-27 12:11:47"
            },
            {
                "id": 3,
                "title": "王二狗1",
                "subtitle": "我是恩的萨1",
                "type": 0,
                "thumbnail": "http://localhost/it/u=2234563230,4026324596&fm=26&gp=0.jpg",
                "read": 1031,
                "content": "遗产纠纷1",
                "order": 1,
                "index_display": 0,
                "note": null,
                "created_at": "2018-12-27 12:12:50",
                "updated_at": "2018-12-27 12:12:50"
            }
        ],
        "first_page_url": "http://video.test/api/admin/article?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://video.test/api/admin/article?page=1",
        "next_page_url": null,
        "path": "http://video.test/api/admin/article",
        "per_page": 15,
        "prev_page_url": null,
        "to": 3,
        "total": 3
    }
}
```
## 文章资讯修改

### 地址：/api/admin/article/{article}

**请求方式：PATCH**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`article`}` | integer | required | 文章id |
| title | string | required | 文章标题 |
| thumbnail | string | required |文章封面图 |
| read | integer | required | 文章浏览量 |
| content | html | optional | 文章内容 |

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
## 文章资讯删除
### 接口地址：/api/admin/article/{article}

**请求方式 DELETE**

**Parameter：**

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
        "message": "操作成功"
    }
}
```

## 资讯浏览记录获取

### 地址：/api/admin/article/view/record

**请求方式：GET**

**Parameter**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 分页数据条数 |
| title | string | optional | 文章标题 |
| use_name | string | optional | 用户姓名 |


**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "message": {
        "current_page": 1,
        "data": [
            {
                "id": 1,
                "article_id": 1,
                "title": "三大",
                "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                "user_name": "123",
                "view_at": "2018-12-27 15:03:36",
                "article": {
                    "id": 1,
                    "title": "王二狗1",
                    "subtitle": "我是恩的萨1"
                },
                "user": {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "test"
                }
            }
        ],
        "first_page_url": "http://video.test/api/admin/article/view/record?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://video.test/api/admin/article/view/record?page=1",
        "next_page_url": null,
        "path": "http://video.test/api/admin/article/view/record",
        "per_page": "15",
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}
```