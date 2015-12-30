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

## O2O HiPOS云端接口

![业务授权](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=566h55CG5ZGYLT4rSGlTaG9w5bqU55SoOiAqUE9T5Lia5YqhKgoADgwAJAVQT1PkupE6IOiOt-WPllRva2VuICjln7rkuo7ln5_lkI0pCgAdCC0tPi0ATA48POi_lOWbnj4-Cmxvb3Ag562J5b6FAEAF5Zue6LCDCiAgICAAZg4AgQ4OACASZW5kAGgKAIE7EFtjYWxsYmFja13mjojmnYMAgSsF6YCa55-lAIFNDgCBJgUAgVQIAIEcCwBwHOaJp-ihjOWFt-S9kwCCKgkARhEAgl8JOiA8POWujOaIkD4-Cg&s=earth)

### 接口调用鉴权（HiShop旗下产品专用）
HiShop旗下自有产品在使用HiPOS接口前，可以通过预先登记的网站域名（主机名）获取授权访问令牌（Token），HiPOS将使用这个Token来识别应用的合法身份。出于安全原因，所有发放给应用的Token都有一定的有效期，请在Token即将过期前重新获取新的Token，以便后续业务的正常调用。

> POST /openapi/token/hishop

路径参数：
> 无

请求参数：
>
| 参数          | 类型      | 说明              | 必填  | 示例                                      |
| :------------ | :-------- | :---------------- | :---- | :---------------------------------------- |
| hostname      | string    | 应用程序主机名    | 是    | www.shop123.com                           |
| notify_url    | string    | Token 通知地址    | 是    | https://www.shop123.com/token_return.ashx |

返回结果：
>
```
// 成功获得授权
{
    "hishop_token_response": {
        "code": 0,
        "msg": "已获取授权并成功通知。",
        "token": "b73fc4a175584f8dd13c267467bd717c1aa270c7"
        "merchant_id": 10011
    }
}
// 无效的应用
{
    "hishop_token_response": {
        "code": 6001,
        "msg": "无效的应用，请检查域名（主机名）是否正确。"
    }
}
// 服务合约已经到期
{
    "hishop_token_response": {
        "code": 6002,
        "msg": "服务合约已经到期，请尽快续约以免影响您的正常业务。"
    }
}
```

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
        "code": 0,
        "msg": "商户资料更新成功。"
    }
}
// 商户不存在
{
    "merchant_update_response": {
        "code": 6011,
        "msg": "该商户不存在，请检查商户号是否正确。"
    }
}
// 提交的资料无效
{
    "merchant_update_response": {
        "code": 6012,
        "msg": "提交的商户资料不合法，请确认资料填写正确。"
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
### [回调]返回授权Token通知
### [回调]设备授权成功通知
### 获取订单详情
### 确认提货


## 独立软件供应商及开发者（ISV）
具备开发及接入能力的合作伙伴与开发者以ISV的身份为商户提供高度可定制的解决方案。

![ISV申请流程](http://www.websequencediagrams.com/cgi-bin/cdraw?lz=dGl0bGUgSVNW55Sz6K-35rWB56iLCklTVi0-K0hpUE9T5ZCI5L2c5LiT5ZGYOiAAIAYKAAkRLT4AGhPotYTotKjlrqHmoLgKYWx0IOWQiOagvAogICAgADASLT4tSVNWOiDpgJrov4fvvIhpc3ZJZCwgaXN2U2VjcmV077yJCmVsc2Ug5ouS57udACcgqbPlm54KZW5k&s=earth)

## ISV专用接口
供ISV向商户提供便捷的服务开通及配置能力，接口列表如下：

### 注册商户
> PUT /v1/isv/{***isvId***}/merchants

路径参数：
>
| 参数        | 类型        | 说明            | 示例                                  |
| :---------- | :---------- | :-------------- | :------------------------------------ |
| isvId       | string      | ISV 唯一标识    | 20151001                              |

请求参数：
>
| 参数        | 类型        | 说明            | 必填  | 示例                                  |
| :---------- | :---------- | :-------------- | :---- | :------------------------------------ |
| name        | string      | 商户名称        | 是    | 海商咖啡                              |
| contact     | string      | 联系人姓名      | 是    | 吕轻候                                |
| mobile      | string      | 手机            | 是    | 18551838888                           |
| telephone   | string      | 电话            |       | 0731-66666666                         |
| email       | string      | 电子邮箱        |       | lvqinghou@163.com                     |
| address     | string      | 地址            |       | 湖南省长沙市芙蓉区韶山北路139号       |

返回结果：
>
```
{
  merchant_id: '1001',
  app_id: 'c4ca4238a0b923820dcc509a6f75849b',
  app_secret: 'c40966e8f40a455425610606561819fa2a578c32',
  expire_at: '2016-11-23 00:59:13'
}
```
