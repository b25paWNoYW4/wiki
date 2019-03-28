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

**说明：is_merchant表示用户身份，false为普通用户，true为商户**

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
| lega_person | string | required,between:2,10 | 公司法人 |
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
| limit | int | nullable | 分页条数 |

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category | 产品所属分类 |
| search | name,category.name | 产品名称，产品所属分类名称 |
| searchFields | name=>'like',category.name=>'=' | 产品名，模糊查询；分类名，精确查询 |

**介绍一下搜索时的参数**

1. search：搜索的参数，可以指定搜索字段，可以多字段同时搜索，如本接口，支持搜索字段为`name`和`category.name`，`?search=xxx`，默认同时搜索这两个字段
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

## 新增分类

### 地址：/v1/client/categories

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 分类名称 |
| parent_id | string | optional | 父级分类id |

**当创建一级分类时不传parent_id参数或传空值，创建二级分类，传对应一级分类的id**

**Example-Response:**
```json
{
    "data": {
        "object": "Category",
        "id": "ao6grd4ed38kyeqz",
        "name": "分类名称235",
        "desc": "235",
        "order": null,
        "created_at": {
            "date": "2019-03-28 14:26:33.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-28 14:26:33.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 8,
        "status": null,
    "meta": {
        "include": [
            "children"
        ],
        "custom": []
    }
}
```

## 新增产品

### 地址：/v1/client/products

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 产品名称 |
| cate_id | string | required | 产品所属分类id |

**只能在二级分类下创建产品，所以上面的cate_id只能为二级分类的id**

**Example-Response:**
```json
{
    "data": {
        "object": "Product",
        "id": "eq6am74064z0vpbn",
        "name": "modelS",
        "created_at": {
            "date": "2019-03-20 15:37:36.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-20 15:37:36.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 4,
        "status": 1,
        "creator": null
    },
    "meta": {
        "include": [
            "category"
        ],
        "custom": []
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