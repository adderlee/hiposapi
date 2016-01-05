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
| notify_url    | string    | Token 通知地址    | 是    | https://www.shop123.com/auth_callback.ashx |

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

<a name="API接口签名规范" />
### API接口签名规范
原始业务数据如：
>a=1&b=2&z=3

加入随机时间码：
>rnd=1447386720779

按字母序形成待签名字符串：
>a=1&b=2&rnd=1447386720779&z=3

将"sign=[App密钥]"拼接到此字符串的最后面，形成：
>a=1&b=2&rnd=1447386720779&z=3&sign=c40966e8f40a455425610606561819fa2a578c32

将此字符串进行SHA1运算，得到签名：
>sign = SHA1('a=1&b=2&rnd=1447386720779&z=3&sign=c40966e8f40a455425610606561819fa2a578c32')

最后向接口POST的数据如下：
>a=1&b=2&rnd=1447386720779&z=3&sign=cf81e8e0d756db9f0e301bf0b64d8525ef3edf85

## O2O HiPOS云端接口

### 更新商户资料
> PUT /openapi/merchants/{***merchant_id***}

路径参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| merchant_id   | string    | 商户号            | 是    | 10011                                     |

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
        "message": "商户资料更新成功。"
    }
}
```

### 更新支付方式
> PUT /openapi/merchants/{***merchantId***}/payments

### 请求设备授权码
> GET /openapi/merchants/{***merchantId***}/stores/{***storeId***}/authcode

### 查询交易统计
> GET /openapi/merchants/{***merchantId***}/stores/{***storeId***}/trades/overview

### 查询交易详情
> GET /openapi/merchants/{***merchantId***}/stores/{***storeId***}/trades/detail

## O2O 应用端接口
### [回调]商户API密钥回调
> POST 方式
示例数据：merchant_id=8&app_id=19244b4cb07d1792bd2fcb5870f841c9&app_secret=c7640bb34ccf3b5335df9383dcc4b195e9a914c8

### [回调]设备授权成功通知
### 获取订单详情
### 确认提货
