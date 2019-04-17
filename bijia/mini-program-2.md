<!-- TITLE: Mini Program 2 -->
<!-- SUBTITLE: A quick summary of Mini Program 2 -->

# 比价小程序-小程序端-doc2-公式部分

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

## 创建自用公式

### 地址：/v1/client/user-formulas

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 公式名称 |
| category_id | string | required | 公式所属分类id |
| product_id | string | required | 公式所属产品id |
| unit_id | string | required | 公式计算结果单位id |
| images | array | required | 公式图片 |
| images.* | url | required | 公式图片url |
| purchase_advice | string | required | 采购建议 |
| content | array | required | 公式内容 |

**分类id只能为二级分类的id**

**Example-Response:**
```json
{
    "data": {
        "object": "Formula",
        "id": "qmv7dk48x5b690wx",
        "name": "公式1",
        "content": [
            {
                "type": 0,
                "value": 2,
                "name": "test"
            }
        ],
        "images": "http://api.apiato.test/storage/image/2019-03-12/NGp8CE1YDopgZxje4pLcyxJMO9b1MfmLTSqWX3qA.jpeg",
        "purchase_advice": "dsfasdf",
        "created_at": {
            "date": "2019-03-14 14:49:35.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-14 14:49:35.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 2,
        "type": null,
        "is_preset": true,
        "status": null,
        "usage": null
    },
    "meta": {
        "include": [
            "category",
            "product",
            "company",
            "unit"
        ],
        "custom": []
    }
}
```



## 公式格式

### 公式介绍

 公式由一个一个元素构成，例如公式 `3a+b-3` ，`3`, `a`, `+`, `b`, `-`, `3`这些就是组成公式的元素；我们定义元素有三种类型：

 - **系数：** 如`3a` 中的 `3` 就定义为系数，可以是整数也可以是小数，但不能是0

 - **操作符：** 如 `+,-,*,/,(,)` ，为了方便，只允许用户使用这几种基本运算符

 - **参数：** 参数这里，考虑到客户的要求，大概有两种，一种是让公式使用者输入的参数，另外一种是公式创建者定义的，带默认值的参数，详细下面会讲


### 公式数据定义

 下面讲下公式具体的定义，每一个元素都需要指定元素的类型，不同类型的元素需要有不同的参数来定义元素属性：

 0. 系数: `{name:"hello",type:0,value:123}` ，type=0表示该元素是系数类型的元素，value表示该系数具体的系数值，value可以是整数或者是小数，但不能为0,name为系数说明

 1. 操作符: `{type:2,operator:"+|-|*|/|(|)"}` ，type=2表示该元素是操作符类型的元素，operator表示该操作符的值，operator只能为`+,-,*,/,(,)` 中的一个,且括号一定要正确合闭

 2. 参数，`{type:1}` type=0表示该元素是系数类型的元素，参数分为3种：
     1. 非预设值类型参数: `{type:1,value_type:0}` value_type=0表示该参数是非预设值类型的参数，预设值参数即需要用户输入的变量，完整定义这个非预设值参数，还需要一个单位属性和说明属性，使用`unit`来定义单位，对应的值为从系统获取的单位的id，name来定义说明，即该元素的含义；一个完整的非预设值参数示例：`{type:1,value_type:0,unit:1,name:"xxx的长度"}`。

     2. 预设值类型参数: 预设值参数是公式创建者预先创建的预设值系列，用户在计算公式时，只能在预设值中选择其中一个;同样需要定义其单位属性、说明属性；示例：`{type:1,value_type:1,unit:2,name:"xxx的长度",optional_list:[{name:"高级",value:10},{name:"中级",value:7}]}` ，optional里定义了可选预设值，每一个可选的预设值由两个属性：name和value，name即可选预设值的说明或名称，value即预设值对应的数值，同样可以是整数和小数

     3. 公式类型参数： 公式类型参数示例 `{type:1,value_type:2,unit:3,name:"yy原料",formula:2,default_value:22}` 这里面的formula是引用的公式，称为客户公式，对应的值是客户公式对应的id，default_value是该公式参数的默认值，在公式不可用时默认调取；但这种公式和现在讲的公式不同，是一种特殊的公式，下面会讲。

 
 一个简单的完整公式的数据：

 ```
 [{"type": 0, "value": 4}, {"type": 2, "operator": "+"}, {"name": "test1", "type": 1, "unit": 2, "value_type": 0}]
 ```
 
### 客户公式

 客户公式和上面的公式差不多，区别在于客户公式没有非预设值类型的参数，且预设值类型的参数的表示和上面的有出入，示例：

 ```
 [{"type": 0, "value": 4}, {"type": 2, "operator": "+"}, {"name": "test1", "type": 1, "unit": 2, "value_type": 1, value:6}]
 ```
 即预设值类型的参数不需要提供可选参数列表`optional_list`,只需要提供`value`


## 创建客户公式

### 地址：/v1/client/customer-formulas

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 公式名称 |
| category_id | string | required | 公式所属分类id |
| product_id | string | required | 公式所属产品id |
| unit_id | string | required | 公式计算结果单位id |
| content | array | required | 公式内容 |

**分类id只能为二级分类的id，客户公式没有需要用户输入的值，详见上一节的说明**

**Example-Response:**
返回示例略，类似上面的创建自用公式

## 修改自用公式

### 地址：/v1/client/user-formulas/`{`ID`}`

**请求方式：PATCH**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 公式名称 |
| category_id | string | required | 公式所属分类id |
| product_id | string | required | 公式所属产品id |
| unit_id | string | required | 公式计算结果单位id |
| images | array | required | 公式图片 |
| images.* | url | required | 公式图片url |
| purchase_advice | string | required | 采购建议 |
| content | array | required | 公式内容 |

**UrlParameter:ID 为待修改公式的id**
**分类id只能为二级分类的id**

**Example-Response:**
略，都是返回修改过的公式内容

## 修改客户公式

### 地址：/v1/client/customer-formulas/`{`ID`}`

**请求方式：PATCH**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 公式名称 |
| category_id | string | required | 公式所属分类id |
| product_id | string | required | 公式所属产品id |
| unit_id | string | required | 公式计算结果单位id |
| content | array | required | 公式内容 |

**UrlParameter:ID 为待修改公式的id**
**分类id只能为二级分类的id**

**Example-Response:**
略，都是返回修改过的公式内容

## 由系统公式创建自用公式

### 地址：/v1/client/user-formulas/by-system-formulas

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| system_formula_no | string | required | 系统公式编号 |
| name | string | required | 公式名称 |
| category_id | string | required | 公式所属分类id |
| product_id | string | required | 公式所属产品id |
| unit_id | string | required | 公式计算结果单位id |
| images | array | required | 公式图片 |
| images.* | url | required | 公式图片url |
| purchase_advice | string | required | 采购建议 |
| content | array | required | 公式内容 |

**分类id只能为二级分类的id，由系统公式创建自用公式，系统公式的内容只能修改不能增删，能修改的只有系数与公式预设**

**Example-Response:**
返回示例略，类似上面的创建自用公式

## 获取自己创建的自用公式

### 地址：/v1/client/user-formulas

示例请求：


**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category,product,unit,company | 公式所属分类；公式所属产品；公式计算结果单位；公式所属公司 |
| search | name,category.name,product.name,company.name | 公式名称，分类名称，产品名称，公司名称 |
| searchFields | name => 'like',category.name => 'like', company.name => 'like',product.name => 'like' | 公式、分类、产品、公司名称，模糊查询； |

**Example-Response:**
略，和搜索公式类似

## 获取自己创建的客户公式

### 地址：/v1/client/customer-formulas

示例请求：


**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category,product,unit,company | 公式所属分类；公式所属产品；公式计算结果单位；公式所属公司 |
| search | name,category.name,product.name,company.name | 公式名称，分类名称，产品名称，公司名称 |
| searchFields | name => 'like',category.name => 'like', company.name => 'like',product.name => 'like' | 公式、分类、产品、公司名称，模糊查询； |

**Example-Response:**
略，和搜索公式类似

## 获取供应商提供的所有客户公式

### 地址：/v1/client/customer-formulas/from-suppliers

*这个接口主要是用在用户创建公式（自用公式）时，填写公式参数选择客户公式用*


**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category,product,unit,company | 公式所属分类；公式所属产品；公式计算结果单位；公式所属公司 |
| search | name,category.name,product.name,company.name | 公式名称，分类名称，产品名称，公司名称 |
| searchFields | name => 'like',category.name => 'like', company.name => 'like',product.name => 'like' | 公式、分类、产品、公司名称，模糊查询； |

**Example-Response:**
略，和搜索公式类似

## 获取提供给指定客户联系人的公式(new)

### 地址：/v1/client/contacts/`{`id`}`/formulas-to-customers



**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category,product,unit,company | 公式所属分类；公式所属产品；公式计算结果单位；公式所属公司 |
| id | 指定客户联系人的id，必填 | 指定客户联系人的id |

**Example-Response:**
略，和搜索公式类似

## 获取指定供应商联系人提供的公式(new)

### 地址：/v1/client/contacts/`{`id`}`/formulas-from-suppliers



**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | category,product,unit,company | 公式所属分类；公式所属产品；公式计算结果单位；公式所属公司 |
| id | 指定供应商联系人的id，必填 | 指定供应商联系人的id |

**Example-Response:**
略，和搜索公式类似

## 删除公式（自用和客户公式）

### 地址：/v1/client/formulas/`{`ID`}`

**请求方式：DELETE**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| id | string | required | 公式ID |

**UrlParameter:ID 为待删除公式的id**
**分类id只能为二级分类的id**

**Example-Response:**
略

# 分组部分

## 新增分组

### 地址：/v1/client/groups

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| name | string | required | 分组名称 |
| type | integer | required | 分组类型，供应商分组0，客户分组1 |

**type一定要传，创建供应商下的分组type=0,客服分组为1**

**Example-Response:**
```json
{
    "data": {
        "object": "Group",
        "id": "bml0wd39b5pkznag",
        "name": "大客户",
        "type": "1",
        "is_default": null,
        "created_at": {
            "date": "2019-03-20 16:53:03.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-20 16:53:03.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 3
    },
    "meta": {
        "include": [
            "contacts"
        ],
        "custom": []
    }
}
```

## 修改分组

### 地址：/v1/client/groups/`{`ID`}`

**请求方式：PATCH**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| ID | string | required | 分组ID |
| name | string | required | 分组名称 |

**只能修改分组名称**

**Example-Response:**
```json
{
    "data": {
        "object": "Group",
        "id": "bml0wd39b5pkznag",
        "name": "大客户会话",
        "type": 1,
        "is_default": false,
        "created_at": {
            "date": "2019-03-20 16:53:03.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "updated_at": {
            "date": "2019-03-20 17:03:15.000000",
            "timezone_type": 3,
            "timezone": "PRC"
        },
        "real_id": 3
    },
    "meta": {
        "include": [
            "contacts"
        ],
        "custom": []
    }
}
```

## 删除分组

### 地址：/v1/client/groups/`{`ID`}`

**请求方式：DELETE**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| ID | string | required | 分组ID |

**只能修改分组名称**

**Example-Response:**
204 no content

## 获取供应商分组

### 地址：/v1/client/supplier-groups



**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | contact | 分组对应的联系人 |


**Example-Response:**
```json
{
    "data": [
        {
            "object": "Group",
            "id": "qnwmkv5704blag6r",
            "name": "默认分组",
            "is_default": true,
            "created_at": {
                "date": "2019-03-11 18:01:09.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "updated_at": {
                "date": "2019-03-11 18:01:10.000000",
                "timezone_type": 3,
                "timezone": "PRC"
            },
            "real_id": 1,
            "contacts": {
                "data": [
                    {
                        "object": "Contact",
                        "id": "qnwmkv5704blag6r",
                        "company_name": "信息科技公司",
                        "contact_origin_name": "Super Admin",
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
                        "real_id": 1
                    }
                ]
            }
        }
    ],
    "meta": {
        "include": [
            "contacts"
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

## 获取客户分组

### 地址：/v1/client/customer-groups



**请求方式：GET**

**需授权：是**

**Parameter:**

| Query Parameter | Optional Values | Description |
| ------ | ------ | ------ |
| include | contact | 分组对应的联系人 |


**Example-Response:**
略，参考上面的

# 联系人部分

## 移动联系人到新分组

### 地址：/v1/client/contacts/`{`ID`}`/move

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| ID | string | required | 联系人的id |
| to_group_id | string | required | 目标分组的id |

**只能移动到相同类型的分组，供应商的分组内的联系人，不能移动到客户的联系人分组里**

**Example-Response:**
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

## 为客户提供公式

### 地址：/v1/client/contacts/`{`ID`}`/set-formulas

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| ID | string | required | 联系人的id |
| formula_id | string | required | 提供的公式的id |

**只能提供给客户公式，且公式只能是自己创建的客户公式**

**Example-Response:**
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

## 取消给客户提供公式

### 地址：/v1/client/contacts/`{`ID`}`/formula-revoke

**请求方式：POST**

**需授权：是**

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| ID | string | required | 联系人的id |
| formula_id | string | required | 提供的公式的id |

**只能提供给客户公式，且公式只能是自己已提供给该用户的客户公式**

**Example-Response:**
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