<!-- TITLE: Mini Program 1 -->
<!-- SUBTITLE: A quick summary of Mini Program 1 -->

# 比价-小程序端-doc1

## 用户登录

### 地址：/v1/client/mini-program/login

**请求方式：POST**

**需授权：否**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| code | string | required | 微信登录凭证code |

*注意code只能使用一次*

**Example-Response:**
```json
{
    "token_type": "Bearer",
    "expires_in": 86400,
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjU2MTVlYWVjNzlmOWJkY2RkN2EwMzVjMjlmOGQ0MDZiOThmYmNjN2MxZmVjNjYzYWNiNWZjNTFlMDZkMTNmOTJlOGFiNTZkYThjYjBhYTIyIn0.eyJhdWQiOiIyIiwianRpIjoiNTYxNWVhZWM3OWY5YmRjZGQ3YTAzNWMyOWY4ZDQwNmI5OGZiY2M3YzFmZWM2NjNhY2I1ZmM1MWUwNmQxM2Y5MmU4YWI1NmRhOGNiMGFhMjIiLCJpYXQiOjE1NTM3NDA0OTIsIm5iZiI6MTU1Mzc0MDQ5MiwiZXhwIjoxNTUzODI2ODkyLCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.BKZkP7fPl6qqB-YLpzxwBpxCOx2yzopL6ISSqjiEVOK1FdGMf7buMFOcKhR40Av5Z8RgnJGuaM6ac9z7nM_KWiCNBGjmyhfLGYShp5O74xuey2duMxxjbG_9g4MIbXJwrXhIuhGUQk2b-sAvmAcn3S_fO2zjGJngit2R7zXubi8viHjlRdZ5fGnheUiRXhlo5lceacnfbH5LEDlLvmkbNIHsZB2GUuWM_5Lcm1Ssj3bFSv05qiDpkhL8bpR7cuhyzRSN2hlF45wgWnV3yPKNfaYemFAQI-ESsmNHqff3JLIXOjHigNOUimzqIUNHBdkF4UjUodjsXv0SFCS2euSrhMt5EPvgRqUWqDTvsa9r5DRuLfD28zHitGkRwHifQTrMGo4xFW3gnUL0D6WAsZQOPqOELuA8WTGxdXcTE-3fG1w8LJtcq2Ch0tlzVVy5lLeyx1vmIoxEPlL-704jrj2egMTcc7FQuK2y2_npuTi51f2EPg5978lmS3zw0jRkrgYX5BkwhKhAzk54k3WshAPW8FdV3768yk63g58ey---zJ5IbHDru4BL9eXrbFRY6CEVcEQrfiTopSCTeuUsKW2isLMdq_wlDLFT5tQoKczzjIcX2QXhInIttTn3m5reArpdKJg_3O9h9MsfEMUVZZ-C8TO0G2CHQWcVArYPGC0XY4g",
    "refresh_token": "def50200de0e68e3027a39da092a4d9728432bb11747c804bd0385c1f14355e849376e209aaef58b4984e58165c1bfd67181c81fbf0fe4cb5ee421a9d372fc17b0c2a8296d76a2ca5ef9acfb4c137cb8240ddf3f26a4cebeb04c59772029e97f8e8a7de94fdabb5f799498597476b76461a5b2b930cf0ea6aa1f4990b81eaa5a8ff27fb8217d6592669e46eaed8fc47fb53f4379f47c5d709c5d171f81706b51f143a8df72761ba82c6c04280bcbbfce8e3d9fa255e76b0d597d66559ebde630ccf9a030e4362ddf73a643b5fcf1ebff052fbe47a3722fd35918f29a2accb2b3ecd50fc464e6b8684ab8cf5b5944eb480b4061cf395e88f1c7100f38ca5f8414e22ec7cc18d7b823e96dbf9d014500805ad83855345bb6b55fd7f7e55edb18716f732cd1c43a6467718ce96c852e3763d950183ee9713a577a402ed42cceb9fce10e2715ce7ded6f03a07752a61f06f2fc146f486b2380dd5b7187f52fa47794de",
    "is_merchant": false
}
```

**说明：is_merchant表示用户身份，~~false为普通用户，true为商户~~ 0为普通用户，1为商户，2为普通用户，审核中，3为普通用户，审核失败**

## 图片上传接口

### 地址：/v1/upload/image

**请求方式：POST**

**需授权：否**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| file | file | required | 图片 |
| editor | int | nullable,in:0,1 | 是否editor |

**当传editor=1时，直接返回图片永久保存地址，主要应用场景如富文本编辑器内；其它情况不需要传editor参数，但返回的地址是暂时的**

**Example-Response:**
```json
{
    "status": "success",
    "status_code": 200,
    "result": {
        "business_code": 9527,
        "data": "http://api.apiato.test/storage/tmp/2019-03-13/Yq45wsr9VQAZxHhBD8wM3XueHzSKgX0bvSexK1fP.jpeg"
    }
}
```

## 更新用户信息

### 地址：/v1/client/mini-program/user-profile

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| nick_name | string | nullable | 微信昵称 |
| avatar_url | url | nullable | 微信头像 |
| gender | integer,in:0,1,2 | nullable | 用户性别 |

*这里的用户信息是调取wx.getUserInfo 获得的*

**Example-Response:**
```json
{
    "data": {
        "object": "User",
        "id": "bml0wd39b5pkznag",
        "name": "1d23aa",
        "email": "asdfsdf",
        "confirmed": false,
        "social_nickname": "prettydog",
        "gender": "2",
        "social_avatar": "http://www.baidu.com",
        "created_at": {
            "date": "2019-03-17 17:34:09.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-04-03 13:55:36.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "readable_created_at": "2 weeks ago",
        "readable_updated_at": "1 second ago"
    },
    "meta": {
        "include": [
            "roles"
        ],
        "custom": []
    }
}
```

## 申请成为商户

### 地址：/v1/client/companies/verify

**请求方式：POST**

**需授权：是**

*说明一下，需授权时，在请求header内加入参数：Authorization：Bearer+空格+access_token, 示例如下*

`Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImY0MTQxMDljMzE5YzQyNmVmMmQxNTEwMzk3NzcxNmQ5ZWJiNDVjMWViYzI1ZDQwNWFiMDZlOTFhMjcyNTM2ZTE4ZjdhNTNmYmFkZWY2MTU1In0.eyJhdWQiOiIyIiwianRpIjoiZjQxNDEwOWMzMTljNDI2ZWYyZDE1MTAzOTc3NzE2ZDllYmI0NWMxZWJjMjVkNDA1YWIwNmU5MWEyNzI1MzZlMThmN2E1M2ZiYWRlZjYxNTUiLCJpYXQiOjE1NTM3NDI0MzksIm5iZiI6MTU1Mzc0MjQzOSwiZXhwIjoxNTUzODI4ODM4LCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.2szgTyOa3ItJPtuDIPbv40Z6EUPq2-lUzcbbuFdk2IhbE5GhM97b0W77WbMwsUwpR-3FSBrhKcU-SPznzONRrVmBvhdjs0QYRPoCexkPEpMgQr1hPnAyObMTxjLnGSW6xfd_aYWCCdbbYAOW0K87HO6aYHnk9zid4pnS-VAvQfzNZYnozAs8j5jK69psjbTAVYDzfJFUMzBy3vj8BmFAUpkIURs8s8XiPv_USMrqwZAu2ns-9s2uGbXbTLtn3pOvtKQyl9KEs9x8eiQRYNEOKNaP7xYAR3eDhiENS2NDrETskkqeeBBx8Nf2dLW3Hfy82wBK9ETXIksFlg4sbLhv8oAYUei2RKqK8mBudR-PBg_gcYC9PBWo7JBSn-5ygWE37nj-LyCrfgUEdhed0aRaeB45t3l0ZgUc50RhsJ_cHkz1ov0N4bo7Vr3XaLjMVNFeVuURAiadeXzRFd_0Ijr_j9XpzIeEfjQce6u98uhuZLA8rKTQW4hy42GPOrP-c0PwrLF-xiB8I60UfVirUDKaC1vKZ3Ph_PAVvsCMxmLWD_17wPlSfg5ae7x11Qyu7RpvnYv_iAYO3a7C6QRaLJ18ry2PFNGYB50n59_7xWiyWoyuaUcVhI4QwEVGqkfCxekhg6_viymCZsztdfKTzNNqVTViI0itA2ueBgbRZ1nz4Cc`

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 公司名称 |
| business | string | required,max:50 | 主营范围 |
| legal_person | string | required,between:2,10 | 公司法人 |
| tel | string | required | 联系电话 |
| address | string | required | 公司地址 |
| company_desc | string | required | 公司介绍 |
| license_images | url | required | 营业执照 |
| logo | url | required | 公司logo |


**Example-Response1:**
```json
{
    "status": "error",
    "status_code": 400,
    "result": {
        "business_code": 1027,
        "error_message": "已认证通过，无法重复认证!"
    }
}
```

**Example-Response2:**
```json
{
    "status": "success",
    "status_code": 200,
    "result": {
        "business_code": 9527,
        "message": "操作成功"
    }
}
```

## 产品搜索

### 地址：/v1/client/products

**请求方式：GET**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| include | string | nullable | 接口可能的关联关系 |
| search | string | nullable | 搜索字段 |
| searchFields | string | nullable | 指定搜索字段的属性 |
| searchJoin | string | nullable | 多条件搜索时，可以指定搜索同时匹配 |
| limit | int | nullable | 分页条数 |

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category | 产品所属分类 |
| search | name,category.name | 产品名称，产品所属分类名称 |
| searchFields | name=>'like',category.name=>'=' | 产品名，模糊查询；分类名，精确查询 |

**介绍一下搜索时的参数**

1. search：搜索的参数，可以指定搜索字段，可以多字段同时搜索，如本接口，支持搜索字段为`name`和`category.name`，`?search=xxx`，默认同时搜索这两个字段
2. searchJoin ：多字段搜索时，如支持搜索A、B、C，默认的是搜索A or B or C条件的结果出来，设置searchJoin=and,结果会是A and B and C
2. searchFields：指定搜索字段的属性，如`?search=xxx&searchFields=category.name:=` category.name:=,表示search的参数是搜索的category.name字段，`:=`表示搜索的参数是搜索与搜索条件相等的结果
3. include：返回数据中可能的关联关系的对应数据，如本接口中category，是产品所属的分类
4. limit: 当limit为0时，不分页返回所有数据

**Example-Response:**

```json
{
    "data": [
        {
            "object": "Product",
            "id": "bml0wd39b5pkznag",
            "name": "小汽车123",
            "created_at": {
                "date": "2019-03-08 09:38:36.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-14 11:45:38.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 3,
            "status": 1,
            "creator": null,
            "category": {
                "data": {
                    "object": "Category",
                    "id": "eq6am74064z0vpbn",
                    "name": "特斯拉",
                    "desc": null,
                    "order": 1,
                    "created_at": {
                        "date": "2019-03-06 10:20:30.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-06 10:20:30.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "real_id": 4,
                    "status": 1,
                    "creator": "平台添加"
                }
            }
        }
    ],
    "meta": {
        "include": [
            "category"
        ],
        "custom": [],
        "pagination": {
            "total": 1,
            "count": 1,
            "per_page": 5,
            "current_page": 1,
            "total_pages": 1,
            "links": []
        }
    }
}
```

## 分类搜索

### 地址：/v1/client/categories

接口默认返回所有一级分类数据，include=children返回每个一级分类的子分类

**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | children | 一级分类的子分类 |
| search | name,children.name | 分类名称，二级分类的名称 |
| searchFields | name=>'like',children.name=>'=' | 分类名称，模糊查询；二级分类的分类名称，模糊查询 |

**Example-Response:**
```json
{
    "data": [        
        {
            "object": "Category",
            "id": "bml0wd39b5pkznag",
            "name": "大汽车",
            "desc": "逻辑代数录放第三方机",
            "order": 1,
            "created_at": {
                "date": "2019-03-06 10:20:05.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-06 10:20:05.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 3,
            "status": 1,
            "creator": "平台添加",
            "children": {
                "data": [
                    {
                        "object": "Category",
                        "id": "dqb9073ap3ekzgrm",
                        "name": "范德萨",
                        "desc": "123",
                        "order": 23,
                        "created_at": {
                            "date": "2019-03-07 03:14:30.000000",
                            "timezone_type": 3,
                            "timezone": "PRC"
                        },
                        "updated_at": {
                            "date": "2019-03-14 10:42:30.000000",
                            "timezone_type": 3,
                            "timezone": "PRC"
                        },
                        "real_id": 5,
                        "status": 1,
                        "creator": "平台添加"
                    }
                ]
            }
        },
    "meta": {
        "include": [
            "children"
        ],
        "custom": [],
        "pagination": {
            "total": 4,
            "count": 4,
            "per_page": 10,
            "current_page": 1,
            "total_pages": 1,
            "links": []
        }
    }
}
```


## 获取单位

### 地址：/v1/client/units

如要直接返回所有数据，设置limit=0

**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| search | name_cn,name_en | 分类中文名称，分类英文名称 |
| searchFields | name_cn=>'like',name_en=>'=' | 分类中文名称，模糊查询；分类英文名称，精确查询 |

**Example-Response:**

```json
{
    "data": [
        {
            "object": "Unit",
            "id": "qnwmkv5704blag6r",
            "name_cn": "长",
            "name_en": "m",
            "real_id": 1,
            "created_at": {
                "date": "2019-03-08 07:16:22.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-08 07:16:22.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            }
        },
        {
            "object": "Unit",
            "id": "qmv7dk48x5b690wx",
            "name_cn": "重",
            "name_en": "kg",
            "real_id": 2,
            "created_at": {
                "date": "2019-03-08 07:16:37.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-08 07:16:37.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            }
        }
    ],
    "meta": {
        "include": [],
        "custom": []
    }
}
```

## 公式搜索

### 地址：/v1/client/formulas

示例请求：
- `http://api.apiato.test/v1/client/formulas?search=name:公式0;category.name:范德萨;product.name:小汽车`
- `http://api.apiato.test/v1/client/formulas?search=name:公式0;category.name:范德萨;product.name:小汽车&include=unit,category,product&searchJoin=and`
- `http://api.apiato.test/v1/client/formulas?search=name:公式;is_preset:1&searchJoin=and` （这个是用来搜索系统预设公式的，由系统预设公式创建用户自建公式时，会用到）

**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category,product,unit,company | 公式所属分类；公式所属产品；公式计算结果单位；公式所属公司 |
| search | name,category.name,product.name,company.name,is_preset | 公式名称，分类名称，产品名称，公司名称，是否平台预设公式 |
| searchFields | name => 'like',category.name => 'like', company.name => 'like',product.name => 'like',is_preset => '=', | 公式、分类、产品、公司名称，模糊查询； |

**Example-Response:**
```json
{
    "data": [
        {
            "object": "Formula",
            "id": "bml0wd39b5pkznag",
            "name": "公式0",
            "content": [
                {
                    "name": "test",
                    "type": 0,
                    "value": 2
                }
            ],
            "images": "http://api.apiato.test/storage/image/2019-03-12/NGp8CE1YDopgZxje4pLcyxJMO9b1MfmLTSqWX3qA.jpeg",
            "purchase_advice": "dsfasdf",
            "created_at": {
                "date": "2019-03-14 17:21:04.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-14 17:21:04.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 3,
            "type": 0,
            "is_preset": true,
            "status": 1,
            "usage": 0
        }
    ],
    "meta": {
        "include": [
            "category",
            "product",
            "company",
            "unit"
        ],
        "custom": [],
        "pagination": {
            "total": 1,
            "count": 1,
            "per_page": 10,
            "current_page": 1,
            "total_pages": 1,
            "links": []
        }
    }
}
```

## 搜索记录&搜索推荐

搜索记录即搜索推荐

### 地址：/v1/client/search-records

示例请求：
- `http://api.apiato.test/v1/client/search-records?limit=5`

**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| limit | int | 一般拿前5条就行 |

**Example-Response:**
```json
{
    "data": [
        {
            "object": "SearchRecord",
            "id": "qnwmkv5704blag6r",
            "key": [
                "看看"
            ],
            "created_at": {
                "date": "2019-03-20 15:13:46.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-20 15:13:46.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 1
        },
				{
            "object": "SearchRecord",
            "id": "bml0wd39b5pkznag",
            "key": [
                "公式0",
                "范德萨",
                "小汽车"
            ],
            "created_at": {
                "date": "2019-03-21 10:27:03.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-21 10:27:03.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 3
        }
    ],
    "meta": {
        "include": [],
        "custom": [],
        "pagination": {
            "total": 14,
            "count": 5,
            "per_page": 5,
            "current_page": 1,
            "total_pages": 3,
            "links": {
                "next": "http://api.apiato.test/v1/client/search-records?limit=5&page=2"
            }
        }
    }
}
```

## 联系人列表

搜索记录即搜索推荐

### 地址：/v1/client/contacts

示例请求：
- `http://api.apiato.test/v1/client/contacts?limit=0`

**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | contact,company | 联系人信息；联系人的公司信息 |
| limit | int | 一般拿全部数据 |

**Example-Response:**
```json
{
    "data": [
        {
            "object": "Contact",
            "id": "qnwmkv5704blag6r",
            "contact_name": "松岛枫",
            "contact_tel": "661",
            "created_at": {
                "date": "2019-03-11 18:02:25.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-11 18:02:26.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 1,
            "company": {
                "data": {
                    "object": "Company",
                    "id": "qnwmkv5704blag6r",
                    "name": "信息科技公司",
                    "business": "科技服务",
                    "legal_person": "王二",
                    "tel": "15221121212",
                    "address": "深圳",
                    "company_desc": "本公司是搞外包的",
                    "license_images": "http://api.apiato.test/storage/image/2019-03-14/Ibee1dhKnB8tvJnygAkfnM02o2YnOpgZqdjN7jKu.jpeg",
                    "created_at": {
                        "date": "2019-03-11 02:07:05.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-14 11:01:09.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "status": 1,
                    "real_id": 1
                }
            },
            "contact": {
                "data": {
                    "object": "User",
                    "id": "qnwmkv5704blag6r",
                    "name": "Super Admin",
                    "email": "admin@admin.com",
                    "confirmed": false,
                    "nickname": null,
                    "gender": null,
                    "birth": null,
                    "social_auth_provider": null,
                    "social_id": null,
                    "social_avatar": {
                        "avatar": null,
                        "original": null
                    },
                    "created_at": {
                        "date": "2019-03-01 10:14:01.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-01 10:14:01.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "readable_created_at": "2 weeks ago",
                    "readable_updated_at": "2 weeks ago",
                    "real_id": 1,
                    "deleted_at": null
                }
            }
        }
    ],
    "meta": {
        "include": [
            "company",
            "contact"
        ],
        "custom": [],
        "pagination": {
            "total": 1,
            "count": 1,
            "per_page": 10,
            "current_page": 1,
            "total_pages": 1,
            "links": []
        }
    }
}
```

## 添加联系人

### 地址：/v1/client/contacts

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| formula_no | string | required | 公式的编号 |


**Example-Response:**
```json
{
    "data": {
        "object": "Contact",
        "id": "eq6am74064z0vpbn",
        "contact_name": "1d23aa",
        "contact_tel": "13551131313",
        "created_at": {
            "date": "2019-03-20 16:21:55.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-20 16:21:55.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 4
    },
    "meta": {
        "include": [
            "company",
            "contact"
        ],
        "custom": []
    }
}
```

## 修改联系人

### 地址：/v1/client/contacts/`{`ID`}`

**请求方式：PATCH**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| contact_name | string | required | 联系人姓名 |
| tel | string | required | 联系人电话 |

*如果需要tel与contact_tel字段一致，联系我修改*

**UrlParameters：ID => 对应联系人的id**


**Example-Response:**
```json
{
    "data": {
        "object": "Contact",
        "id": "w6l8b75dy5qkv9ze",
        "company_name": "张三汽车生产厂",
        "contact_origin_name": "Super Admin",
        "contact_name": "史蒂芬生的",
        "contact_tel": "13135453",
        "created_at": {
            "date": "2019-03-20 16:26:16.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-20 18:19:48.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 7
    },
    "meta": {
        "include": [
            "company",
            "contact"
        ],
        "custom": []
    }
}
```

## 公式询价

### 地址：/v1/client/enquiry-records

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| formula_no | string | required | 公式的编号 |
| contact_name | string | required | 姓名 |
| contact_tel | string | required | 联系方式 |
| contact_company | string | required | 公司名称 |
| need_invoice | boolean | required | 是否需要开票 |


**Example-Response:**
```json
{
    "data": {
        "object": "EnquiryRecord",
        "id": "qnwmkv5704blag6r",
				"order_no": "ER20190325000001KY",
				"contact_name": "王二",
        "contact_tel": "110",
				"contact_company": "楼下小卖部",
        "created_at": {
            "date": "2019-03-20 17:24:42.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-20 17:24:42.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 1
    },
    "meta": {
        "include": [],
        "custom": []
    }
}
```

## 询价记录


### 地址：/v1/client/contacts

示例请求：
- `http://api.apiato.test/v1/client/enquiry-records?include=sender,receiver,product,formula,company`

**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | sender,receiver,product,formula,company | 发送人，接收人，对应产品，对应公式，公式所属公司 |
| limit | int | 一般拿全部数据 |

**Example-Response:**
```json
{
    "data": [
        {
            "object": "EnquiryRecord",
            "id": "qnwmkv5704blag6r",
            "order_no": null,
            "contact_name": "王二",
            "contact_tel": "110",
            "contact_company": "楼下小卖部",
            "has_viewed": 0,
            "created_at": {
                "date": "2019-03-20 17:24:42.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-20 17:24:42.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 1,
            "company": {
                "data": {
                    "object": "Company",
                    "id": "qmv7dk48x5b690wx",
                    "name": "张三汽车生产厂",
                    "business": "汽车",
                    "legal_person": "张三",
                    "tel": "1233124124124",
                    "address": "萨菲",
                    "company_desc": "123",
                    "license_images": null,
                    "created_at": {
                        "date": "2019-03-11 02:07:05.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-14 11:17:22.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "status": 1,
                    "real_id": 2
                }
            },
            "product": {
                "data": {
                    "object": "Product",
                    "id": "qnwmkv5704blag6r",
                    "name": "小汽车dsf",
                    "created_at": {
                        "date": "2019-03-08 09:38:36.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-14 11:45:38.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "real_id": 1,
                    "status": 2,
                    "creator": null
                }
            },
            "sender": {
                "data": {
                    "object": "User",
                    "id": "qnwmkv5704blag6r",
                    "name": "Super Admin",
                    "email": "admin@admin.com",
                    "confirmed": false,
                    "nickname": null,
                    "gender": null,
                    "birth": null,
                    "social_auth_provider": null,
                    "social_id": null,
                    "social_avatar": {
                        "avatar": null,
                        "original": null
                    },
                    "created_at": {
                        "date": "2019-03-01 10:14:01.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-01 10:14:01.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "readable_created_at": "2 weeks ago",
                    "readable_updated_at": "2 weeks ago",
                    "real_id": 1,
                    "deleted_at": null
                }
            },
            "receiver": {
                "data": {
                    "object": "User",
                    "id": "bml0wd39b5pkznag",
                    "name": "1d23aa",
                    "email": "asdfsdf",
                    "confirmed": false,
                    "nickname": null,
                    "gender": null,
                    "birth": null,
                    "social_auth_provider": null,
                    "social_id": null,
                    "social_avatar": {
                        "avatar": null,
                        "original": null
                    },
                    "created_at": {
                        "date": "2019-03-17 17:34:09.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-17 17:34:13.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "readable_created_at": "3 days ago",
                    "readable_updated_at": "3 days ago",
                    "real_id": 3,
                    "deleted_at": null
                }
            },
            "formula": {
                "data": {
                    "object": "Formula",
                    "id": "bml0wd39b5pkznag",
                    "name": "公式0",
                    "content": [
                        {
                            "name": "test",
                            "type": 0,
                            "value": 2
                        }
                    ],
                    "images": "http://api.apiato.test/storage/image/2019-03-12/NGp8CE1YDopgZxje4pLcyxJMO9b1MfmLTSqWX3qA.jpeg",
                    "purchase_advice": "dsfasdf",
                    "created_at": {
                        "date": "2019-03-14 17:21:04.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "updated_at": {
                        "date": "2019-03-14 17:21:04.000000",
                        "timezone_type": 3,
                        "timezone": "PRC"
                    },
                    "real_id": 3,
                    "type": 0,
                    "is_preset": true,
                    "status": 1,
                    "usage": 0
                }
            }
        }
    ],
    "meta": {
        "include": [
            "company",
            "product",
            "sender",
            "receiver",
            "formula"
        ],
        "custom": [],
        "pagination": {
            "total": 1,
            "count": 1,
            "per_page": 10,
            "current_page": 1,
            "total_pages": 1,
            "links": []
        }
    }
}
```

## 公式计算

### 地址：/v1/client/formulas/{ID}/calculate

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| user_input | array | required | 用户输入 |

**说明：将公式解析出来后，按顺序将用户输入的值放到user_input数组中，如果是有预设值的，就将预设值对应的value放到数组中；例如一个公式需要用户输入一个数字，从2个可选值A=>1B=>2选择一个，那么user_input应该为`[22,2]`**


**Example-Response:**
```json
{
    "status": "success",
    "status_code": 200,
    "result": {
        "business_code": 9527,
        "data": {
            "formula_result": "5.00",
            "recommend": [
                {
                    "formula_no": "FN20190321000006DV",
                    "images": "http://api.apiato.test/storage/image/2019-03-12/NGp8CE1YDopgZxje4pLcyxJMO9b1MfmLTSqWX3qA.jpeg",
                    "purchase_advice": "dsfdg3252352asdf",
                    "formula_result": "5.00",
                    "formula_unit": {
                        "name_cn": "重",
                        "name_en": "kg"
                    },
                    "company_name": "信息科技公司"
                }
            ]
        }
    }
}
```

上面由系统公式创建而来的公式，计算结果包含了recommend字段，是查找到的数据，可能有也可能没有