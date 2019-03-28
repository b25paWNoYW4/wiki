<!-- TITLE: Mini Program 2 -->
<!-- SUBTITLE: A quick summary of Mini Program 2 -->

# 比价小程序-小程序端-doc2

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

