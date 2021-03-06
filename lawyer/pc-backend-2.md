<!-- TITLE: PC 后台接口-1 -->
<!-- SUBTITLE: A quick summary of Pc Backend 2 -->

# 系统相关接口
## 用户菜单获取
### 接口地址：/api/admin/menu

**请求方式 GET**

**Parameter：None**

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "message": [
        {
            "id": 1,
            "parent_id": 0,
            "text": "用户管理",
            "icon": "test-icon",
            "link": "test-link",
            "permissions": null,
            "children": [
                {
                    "id": 2,
                    "parent_id": 1,
                    "text": "app用户管理",
                    "icon": "test-icon",
                    "link": "test-link",
                    "permissions": [
                        "admin.mobileUser.index",
                        "admin.mobileUser.update"
                    ]
                },
                {
                    "id": 3,
                    "parent_id": 1,
                    "text": "用户认证管理",
                    "icon": "test-icon",
                    "link": "test-link",
                    "permissions": [
                        "admin.order.index",
                        "admin.order.confirm"
                    ]
                }
            ]
        },
        {
            "id": 7,
            "parent_id": 0,
            "text": "聊天系统",
            "icon": "test-icon",
            "link": "test-link",
            "permissions": null,
            "children": [
                {
                    "id": 9,
                    "parent_id": 7,
                    "text": "客服系统",
                    "icon": "test-icon",
                    "link": "test-link",
                    "permissions": [
                        "admin.message.unRead",
                        "admin.message.getUnRead",
                        "admin.message.send",
                        "admin.message.history"
                    ]
                }
            ]
        }
    ]
}
```

## 系统用户登录
### 接口地址：/api/admin/login

**请求方式 POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| phone | integer | required | 帐号 |
| password | string | required | 密码 |

*当用户角色为客服时，会返回一个csomer_token，这个聊天会用到的*

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "token_type": "Bearer",
            "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImE0YTM4Y2YwODZiZGI3YTZmNmY5YTU0Nzk2MWQ2ZDUwNjQyZWMxY2JhZGNkZGQwMTA4ZmE1MmI2MDgzY2I0NWM3ZmJmNzE4NWM3NWU1NTU4In0.eyJhdWQiOiI3ZGMxZTlmMC1lMTQzLTQwNWItODY0Ni00MzVjNjgwNjYyYjMiLCJqdGkiOiJhNGEzOGNmMDg2YmRiN2E2ZjZmOWE1NDc5NjFkNmQ1MDY0MmVjMWNiYWRjZGRkMDEwOGZhNTJiNjA4M2NiNDVjN2ZiZjcxODVjNzVlNTU1OCIsImlhdCI6MTU0NjM5ODQwNSwibmJmIjoxNTQ2Mzk4NDA1LCJleHAiOjE1Nzc5MzQ0MDUsInN1YiI6IjUxY2Q4YmVkLTk4NGQtNDc4ZS05YWYwLTI4ZmU3ZDMyMmJkYyIsInNjb3BlcyI6W119.WOoy9XsriSiwXjyLwRBED5hlnb8eICnPb93PE4vTAuDuY56TXqiQEwBo-Q4ANqLaL2E0EMrBBA8m-cppo2MXVhGIJs75IILoHHnG-pK0bXM7uyA8MHOrocepYsrVPrcJDwiqW5U6hMIWeyIc6fTZkQDDzKkYAcQudUSQTQhLsEtdMpoy0YgHHgoGxvVLJbdW2Vqej9_fjs2FZbkF8c8sb6dOSeGzmna3Wt70W2BR-d39xoGwG089EpbK9IwMx1yr9rc6gi1Me5Q_4IvUgMVaoTONzXonZVsiQzJcVfr2a2ToZ4fX_ov8W2-D_v6Q88-IjauU_opnjBJ3ITzaZU_8olqu2uFD7cYUUmv08rR0ROtfpsez5zTGGlqLeiQBMOEIMtQgWj4Aj0bdu991dl64O_Br9ygxYk7SxbnZfLjoC28SNkDk4lwT3EPBG__j0_fLY3Aj73XMGfZPqTgN6DLTDUUJgzxoh89WLkOu5O3_C6fAX7cAz9ovWl0ghQKXHmlrfzRx-R-0fv8poYVEebHGE21oyuMkW_dgN27IQSCfDHnDrH8OJRbgpbCuy0_-mHLPhBSAMTgCFC0qotNLlpOsGtslo_oJTPbAbWk3M9srZ_nl6nk13yqL3Z7Oh3sr8PfRKtibRql5WMpJgHYwWYsLZjSdMMwnNA6v00RWU-mqra0",
            "user": {
                "name": "Administrator",
                "phone": "18888888888",
                "avatar": "http://video.test/images/user/default.png",
                "gender": 1,
                "role": {
                    "id": 1,
                    "name": "客服"
                },
                "customer_token": null
            }
        }
    }
}
```

## 用户个人信息获取
### 接口地址：/api/admin/user/profile

**请求方式 GET**

**Parameter：None**

**Example-Response:**

```json
{
    "status": "success",
    "code": 200,
    "message": {
        "id": "3b0e8842-ab2f-4e08-9a7a-4aa17cc4de96",
        "name": "王二狗2",
        "phone": "15882219670",
        "avatar": "http://video.test/images/user/default.png",
        "gender": 1,
        "role": null,
        "customer_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjBjNGI0OWU4MzU2ZDZkZTZhOThiY2U5Y2VkNGY2ZjhhYWU2MGQ3OWEwZDZmN2MyOTkyODAxMDk2Y2RiMTQ1Y2JmZWNmYTNhNGU3ZjFkNDMzIn0.eyJhdWQiOiI3ZGMxZTlmMC1lMTQzLTQwNWItODY0Ni00MzVjNjgwNjYyYjMiLCJqdGkiOiIwYzRiNDllODM1NmQ2ZGU2YTk4YmNlOWNlZDRmNmY4YWFlNjBkNzlhMGQ2ZjdjMjk5MjgwMTA5NmNkYjE0NWNiZmVjZmEzYTRlN2YxZDQzMyIsImlhdCI6MTU0NTcxMDYxNSwibmJmIjoxNTQ1NzEwNjE1LCJleHAiOjE1NzcyNDY2MTUsInN1YiI6ImRiM2NjZDQyLTJiN2QtNGY2Yy05NDFiLWNiNWU1MTg2ZDIzZiIsInNjb3BlcyI6W119.lLn_VIux0XWLfqeBNVI6sQrGjTkueWNJA9Cp7BGwiyyh05Rhc3WSdIzjYk71laDI1L0g9hJduSNx27zSvTOJqJFJA1snfmd31TdgM0VwlFj2GcCtL9csVkTa_H430UvD5ns1eWqVDUUUL8JapFrmmU1HbmDc2-SWUo9kQnElSL4e7eDDCi7xJX_RhyvEjdOv6bTUbat5uLUB-Nizrm7c0pPrE7mboFiCZA83qdPiwPOWZ7ThSMouDtII8HP2jBYOe1JKkd8-9DIl_MqU_gx_LQLX0ZjYnE8ZvzAXgBmlI1unn2hb-l6xyZOEecoFZgArc4jMuPfJ319zwAGy4X7eLcAiS4upKuz32SWgkOu1trVX25bHUjVUxo09bE-7lkh01ABZrlPoENCk6gV2NWzYASTJXSoi6bd0MWSdClgCX15G4_Kdr5ssjaRR6WYs0u5_bbZWHkHy2kwxiG4vBiJTrPITC9L-1D8eTfdrP4UYm56O4t7MDi6n_CTn5w5im9Slqrz47OSjJs-t6185Pj5Pw-NdQcEmkC8v58l3HnTyK0NqPeDI5Bm7_2h6dEBUEP1w4BLbwZfTxgwJ-G933JKtKBc5XYM4mqer03DHwEVuEypnCeNJ3Uj4OTD4yJnBHYiJJwE9aiD8X2aQAfNCeaincQnGU9zby3le2cFo8Q-uuqA"
    }
}
```

## 用户个人信息修改
### 接口地址：/api/admin/user/profile

**请求方式 POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | optional | 用户姓名 |
| password | string | optional | 密码 |
| password_confirm | string | required_if: password | 密码确认 |
| phone | integer | optional | 手机号 |
| avatar | string | optional | 用户头像 |

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

**Example-Response:**


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

## 系统用户创建
### 接口地址：/api/admin/user

**请求方式 POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | optional | 用户姓名1-20位 |
| password | string | optional | 密码 5-32位|
| password_confirm | string | required_if: password | 密码确认 |
| phone | integer | optional | 手机号 |
| avatar | string | optional | 用户头像 |
| role_id | integer | optional | 角色id |

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

## 系统用户更新
### 接口地址：/api/admin/user/{user}

**请求方式 POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`user`}` | string | required | 用户id |
| name | string | optional | 用户姓名1-20位 |
| password | string | optional | 密码 5-32位|
| password_confirm | string | required_if: password | 密码确认 |
| phone | integer | optional | 手机号 |
| avatar | string | optional | 用户头像 |
| role_id | integer | optional | 角色id |

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

## 系统用户删除
### 接口地址：/api/admin/user/{user}

**请求方式 DELETE**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
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

# 系统角色接口
## 角色列表获取
### 接口地址：/api/admin/role

**请求方式 GET**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 分页数据数 |
| id | integer | optional | 角色id |

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
                "name": "客服",
                "guard_name": "admin",
                "permissions": [
                    {
                        "id": 1,
                        "name": "APP端用户获取"
                    },
                    {
                        "id": 2,
                        "name": "APP端用户信息修改"
                    },
                    {
                        "id": 3,
                        "name": "APP端用户认证列表获取"
                    },
                    {
                        "id": 4,
                        "name": "APP端用户认证审核"
                    },
                    {
                        "id": 19,
                        "name": "客服获取未读消息列表"
                    },
                    {
                        "id": 20,
                        "name": "客服获取具体未读消息"
                    },
                    {
                        "id": 21,
                        "name": "客服发送消息"
                    },
                    {
                        "id": 22,
                        "name": "客服获取历史聊天记录"
                    }
                ]
            }
        ],
        "first_page_url": "http://video.test/api/admin/role?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://video.test/api/admin/role?page=1",
        "next_page_url": null,
        "path": "http://video.test/api/admin/role",
        "per_page": 15,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}
```
*参数为id时*
```json
{
    "status": "success",
    "code": 200,
    "message": {
        "id": 1,
        "name": "客服",
        "guard_name": "admin",
        "permission_ids": [
            1,
            2,
            3,
            4,
            19,
            20,
            21,
            22
        ]
    }
}
```

## 权限列表获取
### 接口地址：/api/admin/permission

**请求方式 GET**

**Parameter：None**

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": {
            "app用户管理": [
                {
                    "id": 1,
                    "name": "APP端用户获取"
                },
                {
                    "id": 2,
                    "name": "APP端用户信息修改"
                }
            ],
            "用户认证管理": [
                {
                    "id": 3,
                    "name": "APP端用户认证列表获取"
                },
                {
                    "id": 4,
                    "name": "APP端用户认证审核"
                }
            ],
            "律师团队管理": [
                {
                    "id": 5,
                    "name": "系统律师团队列表获取"
                },
                {
                    "id": 6,
                    "name": "系统律师团队信息创建"
                },
                {
                    "id": 7,
                    "name": "系统律师团队信息更新"
                },
                {
                    "id": 8,
                    "name": "系统律师团队信息删除"
                }
            ],
            "资讯文章管理": [
                {
                    "id": 9,
                    "name": "系统资讯文章信息列表获取"
                },
                {
                    "id": 10,
                    "name": "系统资讯文章信息创建"
                },
                {
                    "id": 11,
                    "name": "系统资讯文章信息更新"
                },
                {
                    "id": 12,
                    "name": "系统资讯文章信息删除"
                }
            ],
            "视频管理": [
                {
                    "id": 13,
                    "name": "系统点播视频信息列表获取"
                },
                {
                    "id": 14,
                    "name": "系统点播视频信息创建"
                },
                {
                    "id": 15,
                    "name": "系统点播视频信息更新"
                },
                {
                    "id": 16,
                    "name": "系统点播视频信息删除"
                }
            ],
            "聊天记录": [
                {
                    "id": 17,
                    "name": "聊天系统信息记录列表获取"
                },
                {
                    "id": 18,
                    "name": "聊天历史记录删除"
                }
            ],
            "客服系统": [
                {
                    "id": 19,
                    "name": "客服获取未读消息列表"
                },
                {
                    "id": 20,
                    "name": "客服获取具体未读消息"
                },
                {
                    "id": 21,
                    "name": "客服发送消息"
                },
                {
                    "id": 22,
                    "name": "客服获取历史聊天记录"
                }
            ],
            "系统用户管理": [
                {
                    "id": 23,
                    "name": "系统用户消息列表获取"
                },
                {
                    "id": 24,
                    "name": "系统用户创建"
                },
                {
                    "id": 25,
                    "name": "系统用户信息更新"
                },
                {
                    "id": 26,
                    "name": "系统用户删除"
                },
                {
                    "id": 27,
                    "name": "系统角色获取"
                }
            ],
            "系统角色管理": [
                {
                    "id": 27,
                    "name": "系统角色获取"
                },
                {
                    "id": 28,
                    "name": "系统角色创建"
                },
                {
                    "id": 29,
                    "name": "系统角色更新"
                },
                {
                    "id": 30,
                    "name": "系统角色删除"
                },
                {
                    "id": 31,
                    "name": "系统权限获取"
                }
            ],
            "系统设置管理": [
                {
                    "id": 32,
                    "name": "系统设置获取"
                },
                {
                    "id": 33,
                    "name": "系统设置修改"
                }
            ]
        }
    }
}
```
## 系统角色创建
### 接口地址：/api/admin/role

**请求方式 POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 角色名 |
| permission_ids | array | required | 对应权限id|


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

## 系统角色更新
### 接口地址：/api/admin/role/{role}

**请求方式 POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 角色名 |
| permission_ids | array | required | 对应权限id|

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

## 系统角色删除
### 接口地址：/api/admin/role/{role}

**请求方式 DELETE**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`role`}` | string | required | 角色id |

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
# APP用户管理接口
## app用户列表获取
### 接口地址：/api/admin/mobile/user

**请求方式 GET**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 每页条数 |
| name | string | optional | 用户姓名 |
| id | string | optional | 用户ID |
| phone | integer | optional | 用户手机 |
| gender | integer | optional | 0女1男 |
| verified | integer | optional | 0未认证1认证 |

**只有通过认证的用户，其对应公司信息才会显示出来**

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
                    "id": "08714e4b-32fd-4bff-846d-c06122dcb7cd",
                    "name": "wangergou",
                    "phone": "13118811351",
                    "avatar": "http://video.test/images/user/default.png",
                    "gender": 1,
                    "verified": 0,
                    "verified_at": null,
                    "created_at": "2019-01-03 17:55:55",
                    "company": null
                },
                {
                    "id": "783d0d37-e09d-4965-9d7d-4126b32914d5",
                    "name": "wangergou",
                    "phone": "13118811353",
                    "avatar": "http://video.test/images/user/default.png",
                    "gender": 1,
                    "verified": 0,
                    "verified_at": null,
                    "created_at": "2019-01-03 17:53:06",
                    "company": null
                },
                {
                    "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "name": "必填王鹅肉",
                    "phone": "18888888880",
                    "avatar": "http://video.test/images/user/default.png",
                    "gender": 1,
                    "verified": 1,
                    "verified_at": "2018-12-29 00:00:00",
                    "created_at": "2018-12-19 17:46:55",
                    "company": {
                        "id": 1,
                        "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "company": "公司名称",
                        "industry": "IT行业",
                        "owner": "所有人",
                        "address": "九里堤",
                        "certificates": [
                            "http://video.test/a.jpg"
                        ],
                        "verified": 1,
                        "verified_at": "2018-12-29 00:00:00",
                        "note": null,
                        "created_at": "2018-12-29 17:30:31",
                        "updated_at": "2018-12-29 17:53:30"
                    }
                },
                {
                    "id": "fbb16a32-ab49-48bf-a45e-13785e4ae6f5",
                    "name": "wangergou",
                    "phone": "13118811352",
                    "avatar": "http://video.test/images/user/default.png",
                    "gender": 1,
                    "verified": 0,
                    "verified_at": null,
                    "created_at": "2019-01-03 16:33:26",
                    "company": null
                }
            ],
            "first_page_url": "http://video.test/api/admin/mobile/user?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/admin/mobile/user?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/admin/mobile/user",
            "per_page": 15,
            "prev_page_url": null,
            "to": 4,
            "total": 4
        }
    }
}
```

## app用户信息修改
### 接口地址：/api/admin/mobile/user/{user}

**请求方式 PATCH**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`user`}` | string | rquired | 用户id |
| name | string | optional | 用户姓名 |
| password | string | optional | 密码 |
| password_confirm | string | required_if: password | 密码确认 |
| verified | integer | optional | 0未认证1认证 |

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

# 用户认证管理接口
## 用户管理列表获取
### 接口地址：/api/admin/order

**请求方式 GET**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| limit | integer | optional | 每页条数 |
| id | string | optional | orderID |

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
                    "order_no": "12312412",
                    "status": 1,
                    "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                    "company_id": 1,
                    "state": 0,
                    "order_completed_at": null,
                    "created_at": "2018-12-29 17:27:44",
                    "updated_at": "2018-12-29 17:37:52",
                    "company": {
                        "id": 1,
                        "user_id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "company": "公司名称",
                        "industry": "IT行业",
                        "owner": "所有人",
                        "address": "九里堤",
                        "certificates": [
                            "http://video.test/a.jpg"
                        ],
                        "verified": 1,
                        "verified_at": "2018-12-29 00:00:00",
                        "note": null,
                        "created_at": "2018-12-29 17:30:31",
                        "updated_at": "2018-12-29 17:37:52"
                    },
                    "user": {
                        "id": "ce8a75d0-47b3-4cee-bdaf-a254b76d0764",
                        "name": "必填王鹅肉"
                    }
                }
            ],
            "first_page_url": "http://video.test/api/admin/order?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://video.test/api/admin/order?page=1",
            "next_page_url": null,
            "path": "http://video.test/api/admin/order",
            "per_page": 15,
            "prev_page_url": null,
            "to": 1,
            "total": 1
        }
    }
}
```
*参数解释*

```text
工单状态
status = 0 => 待处理
status = 1 => 已完成
工单处理结果
state = 0 => 审核未处理
state = 1 => 审核通过
state = 2 => 审核不通过
```
## 用户认证审核
### 接口地址：/api/admin/order/{order}

**请求方式 PATCH**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| `{`order`}` | string | rquired | orderid |
| state | integer | required | 1审核通过2审核不通过 |

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

**Parameter：**

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
| APP_Version | string | required | app版本号 |
| APP_Download_Url | string | required | app下载地址 |
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

## 文件上传

### 地址：/api/upload/file

**请求方式：POST**

**Parameter：**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| file | file | required | 文件，只能为apk格式 |

**Example-Response:**
```json
{
    "status": "success",
    "code": 200,
    "result": {
        "statusCode": 200,
        "message": "https://xinyuan.uiit.org/storage/file/2019-02-14/6zDjP80ML9j4M98q.apk"
    }
}
```