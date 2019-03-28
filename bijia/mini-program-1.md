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

## 申请成为商户

### 地址：/v1/client/companies/verify

**请求方式：POST**

**需授权：是**

*说明一下，需授权时，在请求header内加入参数：Authorization：Bearer+空格+access_token, 示例如下*

`Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImY0MTQxMDljMzE5YzQyNmVmMmQxNTEwMzk3NzcxNmQ5ZWJiNDVjMWViYzI1ZDQwNWFiMDZlOTFhMjcyNTM2ZTE4ZjdhNTNmYmFkZWY2MTU1In0.eyJhdWQiOiIyIiwianRpIjoiZjQxNDEwOWMzMTljNDI2ZWYyZDE1MTAzOTc3NzE2ZDllYmI0NWMxZWJjMjVkNDA1YWIwNmU5MWEyNzI1MzZlMThmN2E1M2ZiYWRlZjYxNTUiLCJpYXQiOjE1NTM3NDI0MzksIm5iZiI6MTU1Mzc0MjQzOSwiZXhwIjoxNTUzODI4ODM4LCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.2szgTyOa3ItJPtuDIPbv40Z6EUPq2-lUzcbbuFdk2IhbE5GhM97b0W77WbMwsUwpR-3FSBrhKcU-SPznzONRrVmBvhdjs0QYRPoCexkPEpMgQr1hPnAyObMTxjLnGSW6xfd_aYWCCdbbYAOW0K87HO6aYHnk9zid4pnS-VAvQfzNZYnozAs8j5jK69psjbTAVYDzfJFUMzBy3vj8BmFAUpkIURs8s8XiPv_USMrqwZAu2ns-9s2uGbXbTLtn3pOvtKQyl9KEs9x8eiQRYNEOKNaP7xYAR3eDhiENS2NDrETskkqeeBBx8Nf2dLW3Hfy82wBK9ETXIksFlg4sbLhv8oAYUei2RKqK8mBudR-PBg_gcYC9PBWo7JBSn-5ygWE37nj-LyCrfgUEdhed0aRaeB45t3l0ZgUc50RhsJ_cHkz1ov0N4bo7Vr3XaLjMVNFeVuURAiadeXzRFd_0Ijr_j9XpzIeEfjQce6u98uhuZLA8rKTQW4hy42GPOrP-c0PwrLF-xiB8I60UfVirUDKaC1vKZ3Ph_PAVvsCMxmLWD_17wPlSfg5ae7x11Qyu7RpvnYv_iAYO3a7C6QRaLJ18ry2PFNGYB50n59_7xWiyWoyuaUcVhI4QwEVGqkfCxekhg6_viymCZsztdfKTzNNqVTViI0itA2ueBgbRZ1nz4Cc`

**Parameter:**

| Parameter | Type | Status | Description |
| ------ | ------ | ------ | ------ |
| code | string | required | 微信登录凭证code |
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
