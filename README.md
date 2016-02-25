# HiPOS Open API
>HiPOS 提供高效线易用的线下支付及相关业务的移动互联网O2O领域解决方案，HiPOS 开放平台向所有具备开发及接入能力的合作伙伴与开发者提供完整的业务接口，旨在鼓励商业模式和客户体验的创新与改进。

## 特点
1. 所有接口均通过HTTP SSL（[HTTPS](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%AE%89%E5%85%A8%E5%8D%8F%E8%AE%AE)）安全通道使用，确保安全性和可靠性。
2. 接口最大程度采用 [REST](https://zh.wikipedia.org/wiki/REST) 风格，简单易用。
3. 接口返回数据统一使用 [json](https://zh.wikipedia.org/wiki/JSON) 格式。

## 支持的 O2O 应用场景
### 商户资料及支付设置

![商户资料及支付设置](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=566h55CG5ZGYLT4r5LqR5ZWG5Z-OOiDllYbmiLforr7nva4KAA8JLT4AFwyvvOWFpeaUr-S7mAAXEitIaVBPU-S6kTog5pu05pawAEsHtYTmlpkKABUILS0-LQBrCzw86L-U5ZuePj4ALh0AZw0AHywtPi0AgWcJOiA8POWujOaIkD4-&s=earth)

### 门店增加POS机

![门店增加POS机](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=566h55CG5ZGYLT4r5LqR5ZWG5Z-OOiDlop7liqBQT1PmnLoKAA8JLT4AGAvnoa7lrprpl6jlupcAFwwrSGlQT1PkupE6IOivt-axguiuvuWkh-aOiOadg-eggQoAGAgtLT4tAGgLPDzov5Tlm54-Pgpsb29wIOetieW-heWbnuiwgwogICAgAHAXABsMZW5kAFUKAIFEDVtjYWxsYmFja10AgQMM5oiQ5Yqf6YCa55-lAIFcCy0-LQCBOwoAgQ0LABUNAIIxCTogPDwAgiQMAE8GPj4&s=earth)

### 扫码提货

![扫码提货](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=5Yiw5bqX6aG-5a6iLT4rUE9T5py6OiDmiavnoIHmj5DotKcKAA8GLT4rSGlQT1PkupE6IAAUBuS6pOaYkwoADwgtPivkupHllYbln446IOiOt-WPluiuouWNleeKtuaAgQoAFQktLT4tAEMKPDwAGgw-PgphbHQg5bCa5pyq5pSv5LuYCiAgICAAWwsAgR4I57q_5LiL5LuY5qy-AB8FAIEiCACBPwjlpITnkIYADxIAcA8APAblrozmiJA-PgplbmQAgT0X56Gu6K6kAIIQBwCBNRnmiJDlip8-PgCCDwotPi0AglEJAIJPBQAdBgCCUggtPi0AgnwMOiA8PACBBAk&s=earth)

### 查询交易信息

![查询交易信息](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=566h55CG5ZGYLT4r5LqR5ZWG5Z-OOiDmn6XnnIvkuqTmmJMKAA8JLT4rSGlQT1PkupEAHgXor6Lpl6jlupflj4oAEgWk5piT57uf6K6hCgAhCC0tPi0ATgs8PAAaDD4-Cm9wdCB0ZXh0CiAgICAAThwAgQcG6K-m5oOFACgFAEMfACQGPj4KZW5kAIE4Cy0-LQCBawk6IDw85a6M5oiQPj4K&s=earth)

## 接口返回错误信息格式
>
```
{
    "error": {
        "code": 1001,
        "message": "缺少必须的参数或参数值无效！"
    }
}
```

## API鉴权（HiShop旗下产品专用）
HiShop旗下自有产品在使用HiPOS接口前，可以通过预先登记的网站域名（主机名）获取授权访问令牌（Token），HiPOS将使用这个Token来识别应用的合法身份。出于安全原因，所有发放给应用的Token都有一定的有效期，请在Token即将过期前重新获取新的Token，以便后续业务的正常调用。

![获取商户API密钥](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=SGlTaG9w5bqU55SoLT4rSGlQT1PkupE6IOiOt-WPluWVhuaIt0FQSeWvhumSpSAo5Z-65LqO5Z-f5ZCNKQoAJwgtLT4tAD4MOiA8POi_lOWbnj4-Cmxvb3Ag562J5b6F5Zue6LCDCiAgICAAaw4ALw4AIA1lbmQAXgo-KwBZDltjYWxsYmFja10AgRsPAGMHAIFSDQCBIAUAgVgIAIEWCw&s=earth)

### 获取商户API密钥
> POST /openapi/auth/hishop

路径参数：
> 无

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| hostname      | string    | 应用程序主机名    | 是    | www.shop123.com                           |
| notify_url    | string    | Token 通知地址    | 是    | https://www.shop123.com/auth_callback.ashx|

返回结果：
>
```
// 成功获得密钥
{
    "hishop_auth_response": {
        "message": "已获取授权密钥并成功通知。",
        "notify_url": "http://www.shop123.com/auth_callback.ashx"
    }
}
```

### 获取Access Token
在正式调用业务接口前需要通过OAuth2获得**Access Token**，并且具有一定的有效期，再次调用业务接口前需要检查**Access Token**是否已经**过期**，否则需要重新获取。
> POST /openapi/token

调用参数：

HTTP请求头中将 app_id 与 app_secret使用“:”拼接后使用**Base64**编码，使用**[HTTP基本认证](https://zh.wikipedia.org/wiki/HTTP%E5%9F%BA%E6%9C%AC%E8%AE%A4%E8%AF%81)**

```
Authorization: Basic YzRjYTQyMzhhMGI5MjM4MjBkY2M1MDlhNmY3NTg0OWI6YzQwOTY2ZThmNDBhNDU1NDI1NjEwNjA2NTYxODE5ZmEyYTU3OGMzMg==
grant_type=client_credentials
```

正确返回数据：
```
{
  "token_type": "bearer",
  "access_token": "f7420dad8e471ab7df0f6b4b646f9010aea3e131",
  "expires_in": 3600
}
```

## O2O HiPOS云端接口

### 更新商户资料
> PUT /openapi/merchants/{***merchant_id***}

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| name          | string    | 商户名称          | 是    | 海商咖啡                                  |
| contact       | string    | 联系人            | 是    | 吕轻候                                    |
| mobile        | string    | 手机号码          | 是    | 18866667777                               |

返回结果：
>
```
// 更新成功
{
    "merchant_update_response": {
        "expire_at": "2017-01-11T09:07:30.904Z"
    }
}
```

### 更新 HiShopO2O 功能接口设置
> PUT /openapi/merchants/{***merchant_id***}/hishopo2o

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| authqr        | string    | 设备授权回调      | 是    | https://www.shop123.com/authqr.ashx       |
| status        | string    | 订单状态接口      | 是    | https://www.shop123.com/tr_status.ashx    |
| confirm       | string    | 订单确认接口      | 是    | https://www.shop123.com/tr_confirm.ashx   |

返回结果：
>
```
// 更新成功
{
    "merchant_hishopo2o_response": {
        "message": "HiShopO2O设置更新成功。"
    }
}
```

### 获取支付宝开发者公钥
> GET /openapi/merchants/{***merchant_id***}/alipaykey

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |

请求参数：
> 无

返回结果：
>
```
// 成功
{
    "merchant_alipaykey_response": {
        "public_key": "MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC+gYLp1daQKQhD944C40KQV9SULDzXwHkcyhrJuGJGfRIeGyVVs4BFtR/m6LWOPiClb4FSP8BOP3fOOY76M75n8NRImJf47LtJ8qLHhtKiz/DphHn56mSRDo6IKxrzsWfMxwWeIOaFcFggvmOGjlq++/JtrnM3k6iHwvXj3KkVTwIDAQAB"
    }
}
```

### 更新支付方式
> PUT /openapi/merchants/{***merchant_id***}/payments

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| ali_app_id    | string    | 支付宝AppId       | 是    | 2015101700468946                          |
| wx_app_id     | string    | 公众号AppId       | 是    | wx7afb8b71daee6a13                        |
| wx_mch_id     | string    | 微信支付商户号    | 是    | 1277664401                                |
| wx_pay_secret | string    | 微信支付API密钥   | 是    | fd70927a9800def8c49XXXXXXXXXXXXX          |
| wx_pay_cert   | string    | 微信支付证书(B64) | 是    | MIILOAIBAzCCCwIGCSqGSIb3DQEHAaCCCvME..... |

返回结果：
>
```
// 更新成功
{
    "merchant_payments_response": {
        "message": "支付设置更新成功。"
    }
}
```

### 请求生成设备授权码
> POST /openapi/merchants/{***merchant_id***}/hishop/authcode

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| store_name    | string    | 门店名称          | 是    | 大剧院店                                  |

返回结果：
>
```
// 调用成功返回授权二维码
{
    "merchant_authcode_response": {
        "qr": "WCusK9uPh4HraXO1QFectz61OTo="
    }
}
```

### 查询交易统计
> GET /openapi/merchants/{***merchant_id***}/hishop/trades

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| store_name    | string    | 门店名称          | 否    | 大剧院店                                  |
| from          | string    | 开始日期          | 否    | 20151017                                  |
| to            | string    | 截止日期          | 否    | 20151116                                  |
| page          | number    | 当前页码          | 否    | 1                                         |
| page_size     | number    | 每页返回数量      | 否    | 10                                        |

返回结果：
>
```
{
    "merchant_trades_response": {
        "page": 1,
        "page_size": 10,
        "items_count": 2,
        "total": 0.18,
        "count": 10,
        "detail": [
            {
                "id": "56937a63d5c8c66e0948f58f",
                "name": "望京SOHO店",
                "total": 0.13,
                "count": 5,
                "devices": [
                    {
                        "device_id": "3826ef14abfa52ca",
                        "total": 0.13,
                        "count": 5
                    }
                ]
            },
            {
                "id": "56937a49d5c8c66e0948f58e",
                "name": "大剧院店",
                "total": 0.05,
                "count": 5,
                "devices": [
                    {
                        "device_id": "3826ef14abfa52ca",
                        "total": 0.05,
                        "count": 5
                    }
                ]
            }
        ]
    }
}
```

### 查询交易详情
> GET /openapi/merchants/{***merchant_id***}/hishop/trades/store/{***store_id***}/detail

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 9                                         |
| store_id      | string    | 门店编号          | 是    | 56937a49d5c8c66e0948f58e                  |

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| device_id     | string    | 设备编号          | 否    | 3826ef14abfa52ca                          |
| hishop_only   | boolean   | 仅限商城订单      | 否    | true                                      |
| code          | string    | 提货单号          | 否    | YSC1453104690                             |
| from          | string    | 开始日期          | 是    | 20151017                                  |
| to            | string    | 截止日期          | 是    | 20151116                                  |
| page          | number    | 当前页码          | 否    | 1                                         |
| page_size     | number    | 每页返回数量      | 否    | 10                                        |

返回结果：
>
```
{
    "merchant_trades_detail_response": {
        "page": 1,
        "page_size": 10,
        "items_count": 5,
        "detail": [
            {
                "created_at": "2016-01-18T08:50:54.522Z",
                "code": "YSC1453104690",
                "amount": 0.01,
                "method": "weixin",
                "tid": "8600001300000100000048",
                "paid_at": "2016-01-18T08:52:48.980Z",
                "device_id": "3826ef14abfa52ca",
                "method_alias": "微信"
            },
            {
                "created_at": "2016-01-19T05:58:05.071Z",
                "code": "YSC1453183009",
                "amount": 0.01,
                "method": "cash",
                "tid": "8600001300000100000049",
                "paid_at": "2016-01-19T05:58:08.165Z",
                "device_id": "3826ef14abfa52ca",
                "method_alias": "现金"
            },
            {
                "created_at": "2016-01-19T05:59:07.487Z",
                "code": "YSC1453183009",
                "amount": 0.01,
                "method": "cash",
                "tid": "8600001300000100000050",
                "paid_at": "2016-01-19T05:59:19.462Z",
                "device_id": "3826ef14abfa52ca",
                "method_alias": "现金"
            },
            {
                "created_at": "2016-01-19T06:00:22.180Z",
                "code": "YSC1453183009",
                "amount": 0.01,
                "method": "cash",
                "tid": "8600001300000100000051",
                "paid_at": "2016-01-19T06:00:24.180Z",
                "device_id": "3826ef14abfa52ca",
                "method_alias": "现金"
            },
            {
                "created_at": "2016-01-19T06:00:46.943Z",
                "code": "YSC1453183009",
                "amount": 0.01,
                "method": "weixin",
                "tid": "8600001300000100000052",
                "paid_at": "2016-01-19T06:01:30.842Z",
                "device_id": "3826ef14abfa52ca",
                "method_alias": "微信"
            }
        ]
    }
}
```

## O2O 应用端接口
### [回调]商户API密钥回调
> POST 方式
示例数据：merchant_id=8&app_id=19244b4cb07d1792bd2fcb5870f841c9&app_secret=c7640bb34ccf3b5335df9383dcc4b195e9a914c8

### [回调]设备授权回调
> POST 方式
示例数据：device_id=3826ef14abfa52ca&store_name=大剧院店&new=true

### 获取订单详情
> GET 方式

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| code          | string    | 提货单号          | 是    | YSC20110118                               |
| device_id     | string    | 设备编号          | 是    | 3826ef14abfa52ca                          |

返回结果：
>
```
{
    "order_info_response": {
        "id": "20160113000011121",
        "detail": "好人沙发（超软版）黑色"
        "amount": "188.68",
        "paid": "true"
    }
}
```

### 确认提货
> POST 方式

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| code          | string    | 提货单号          | 是    | YSC20110118                               |
| device_id     | string    | 设备编号          | 是    | 3826ef14abfa52ca                          |

返回结果：
>
```
{
    "confirming_response": {
        "result": "ok"
    }
}
```
