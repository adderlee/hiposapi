# HiPOS Open API
>HiPOS 提供高效线易用的线下支付及相关业务的移动互联网O2O领域解决方案，HiPOS 开放平台向所有具备开发及接入能力的合作伙伴与开发者提供完整的业务接口，旨在鼓励商业模式和客户体验的创新与改进。

## 特点
1. 所有接口均通过HTTP SSL（[HTTPS](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%AE%89%E5%85%A8%E5%8D%8F%E8%AE%AE)）安全通道使用，确保安全性和可靠性。
2. 接口最大程度采用 [REST](https://zh.wikipedia.org/wiki/REST) 风格，简单易用。
3. 接口返回数据统一使用 [json](https://zh.wikipedia.org/wiki/JSON) 格式。

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
