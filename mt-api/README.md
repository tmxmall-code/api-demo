# 机器翻译API简介

机器翻译API，是Tmxmall为了响应用户号召，提供目前通用领域的机器翻译引擎的集成服务。目的是为了降低用户使用机器翻译的成本，只需要注册一个账号，即可使用各种各样的机器翻译服务。除了以上优点，用户可在Tmxmall个人中心完成机器翻译引擎一键切换，省事省心。目前Tmxmall机器翻译API已集成到YiCAT、memoQ 8.6、SDL Trados 2014、2015、2017、2019中。



![](/assets/mt-banner.png)

# API接口

## 引擎选择接口URL

```
http://api.tmxmall.com/v1/http/setmtprovider?mt_provider=XXXX&mt_field=ecomerce&user_name=XXX&client_id=d0c78b242894a032cb8c3aa7483284b4&de=trados
```

输入参数:

| 参数名称 | 说明 | 参数类型 | 是否为空 |
| :---: | :---: | :---: | :---: |
| user\_name | 用户Tmxmall邮箱账号 | 字符 | N |
| client\_id | 用户clientId | 字符 | N |
| de | 调用方 | 字符 | Y |
| mt\_provider | 选择的引擎 | 字符 | N |
| mt\_filed | 领域 | 字符 | Y |

返回参数:

| 参数名称 | 含义 | 说明 |
| :---: | :---: | :---: |
| error\_code | 错误码 | 错误码，0表示正常返回，如果使用不当或者系统出错会返回TB打头的错误码 |
| error\_msg | 错误提示信息 | 错误提示信息 |

可选引擎列表和垂直领域:

| 引擎的名称 | 输入参数 | 支持的领域 | 输入参数 | 支持的语种 |
| :---: | :---: | :---: | :---: | :---: |
| 谷歌 | Google | 通用 | general | 支持中文（简/繁）、英语、俄语、阿拉伯语、法语、德语、菲律宾语、柬埔寨语、老挝语、韩语、马来语、印尼语、缅甸语、西班牙语、越南语、希腊语、日语、葡萄牙语、意大利语、泰语任意语言双向互译。 |
| 腾讯翻译君 | Fanyijun | 通用 | general | 支持中-英、中-日、中-韩、中-法、中-西、中-德、中-俄、中-葡、中-越、中-印尼、中-泰、中-马来、英-法、英-西、英-德、英-俄、英-葡、英-越、英-印尼、英-泰、英-马来、法-西、法-德、法-俄、法-葡、西-德、西-俄、西-葡、德-俄、德-葡、俄-葡双向互译。 |
| 阿里翻译 | AliTrans | 通用、电商 | general, ecommerce | 通用领域支持中-英双向互译，电商领域支持中文简体、英文、俄语、葡萄牙语、西班牙语、法语任意语言双向互译。 |
| 百度翻译 | Baidu | 通用 | general | 支持中文（简/繁）、英文、阿拉伯语、德语、俄语、法语、韩语、葡萄牙语、日语、泰语、西班牙语、希腊语、越南语任意语言双向互译。 |
| 有道翻译 | Youdao | 通用 | general | 支持中-英、中-日、中-韩、中-法、中-俄、中-西、中-葡双向互译。 |
| 搜狗翻译 | Sogou | 通用 | general | 支持中文（简/繁）、英文、阿拉伯语、德语、俄语、法语、菲律宾语、韩语、马来语、葡萄牙语、日语、泰语、西班牙语、希腊语、印尼语、越南语任意语言双向互译。 |
| 小牛翻译 | NiuTrans | 通用 | general | 支持中-英、中-日、中-韩、中-泰双向互译。 |
| 新译 | NewTrans | 机械工程，金融财经，新闻传媒，法律合同，旅游口语，知识产权，IT通讯，生物医学 | engine，finance，news，laws，spoken，patent，it，medicine | 支持中英互译 |
| | | | | |

## 翻译调用接口URL

```
http://api.tmxmall.com/v3/http/mttranslate?text=XXXX&user_name=XXX&from=zh-CN&to=en-US&sign=xxx&mtPeovider=Baidu
```

输入参数:

| 参数名称 | 说明 | 参数类型 | 是否为空 |
| :---: | :---: | :---: | :---: |
| user\_name | 用户Tmxmall邮箱账号 | 字符 | N |
| sign | 签名 | 字符 | N |
| mtPeovider | 翻译引擎 | 字符 | N |
| text | 检索内容 | 字符 | N |
| from | 源语言 | 字符 | N |
| to | 目标语言 | 字符 | N |

> 说明：签名要通过此方式生成：String sign = DigestUtils.md5Hex(user_name + from + text + to + clientId);

语言列表：

| 语言简写 | 名称 |
| :---: | :---: |
| zh-CN | 中文简体 |
| zh-TW | 中文台湾 |
| zh-HK | 中文香港 |
| en-US | 英语美国 |
| en-GB | 英语英国 |
| ja-JP | 日语 |
| ko-KR | 韩语 |
| ru-RU | 俄语 |
| de-DE | 德语 |
| es-ES | 西班牙语 |
| fr-FR | 法语 |
| pt-PT | 葡萄牙语 |
| ar-SD | 阿拉伯语 |
| th-TH | 泰语 |
| vi-VN | 越南语 |
| my-MM | 缅甸语 |
| id-ID | 印尼语 |
| km-KH | 高棉语 |
| lo-LA | 老挝语 |
| ms-MY | 马来西亚语 |
| fil-P | 菲律宾语 |
| el-GR | 希腊语 |
| it-IT | 意大利语 |
| tr-TR | 土耳其语 |
| uk-UA | 乌克兰语 |
| sv-SE | 瑞典语 |
| cs-CZ | 捷克语 |
| sk-SK | 斯洛伐克语 |
| sl-SL | 斯洛文尼亚语 |
| pl-PL | 波兰语 |
| da-DK | 丹麦语 |
| nl-NL | 荷兰语 |
| fi-FI | 芬兰语 |
| hu-HU | 匈牙利语 |
| hi-IN | 印地语 |
| he-IL | 希伯来语 |
| bn-BD | 孟加拉语 |
| hy-AM | 亚美尼亚语 |
| bo-CN | 藏语 |
| ug-CN | 维语 |
| ii-CN | 彝语 |
| la-00 | 拉丁语 |
| ro-RO | 罗马尼亚语 |
| bg-BG | 保加利亚语 |
| hr-HR | 克罗地亚语 |
| sq-AL | 阿尔巴里亚语 |
| mk-MK | 马其顿语 |
| et-EE | 爱沙尼亚语 |
| lt-LT | 立陶宛语 |

> 说明：client\_id即为tmxmall的API Key，client\_id需要登录到Tmxmall网站个人中心查看。

返回参数:

| 参数名称 | 含义 | 说明 |
| :---: | :---: | :---: |
| error\_code | 错误码 | 错误码，0表示正常返回，如果使用不当或者系统出错会返回TB打头的错误码 |
| error\_msg | 错误提示信息 | 错误提示信息 |
| from | 源语言（同参数表） | 输入句子或术语的语言编码 |
| to | 目标语言（同参数表） | 输出句子或术语的语言编码 |
| mt\_set | 数组，机器翻译结果集合 | 返回机器翻译的集合 |
| mt\_set结构： | | |
| 参数名称 | 含义 | 说明 |
| src | 同text | TB打头的错误码 |
| tgt | 机器翻译译文 | |
| provider | 机器翻译供应商 | 目前支持谷歌、百度、有道、搜狗，可以在个人中心设置 |

错误码说明:

| 错误码 | 错误说明 |
| :---: | :---: |
| 0 | client\_id验证通过 |
| TB01002 | 系统错误 |
| TB01001 | 参数不合法\(包括clientId不匹配\) |
| TB01021 | 用户名不存在 |
| TB01072 | 当前启用的机器翻译不支持该语言对 |
| TB01073 | 余额不够扣减 |
| TB01074 | 今日消费已超限 |

返回数据为json格式，示例如下：

```
{"error_code":"0","error_msg":"成功","from":"zh-CN","to":"en-US","text":"你好","mt_set":[{"src":"你好","tgt":"Hello,","provider":"Baidu"}]}
```

其他异常情况:

验证接口超时时间为5秒，5秒无信息返回，可认为是Tmxmall网站超时或者是网络超时。

# 用户ClientId验证接口

机器翻译api集成商在用户设置账号的时候需要验证账号信息是否正确。验证接口如下：

### 接口URL

`http://api.tmxmall.com/v1/http/clientIdVerify?user_name=XXXX&client_id=12334455&de=trados`

> get请求，无需用户登录

### 输入参数

| 参数名称 | 说明 | 参数类型 | 是否为空 |
| :---: | :---: | :---: | :---: |
| user\_name | 用户Tmxmall邮箱账号 | 字符 | N |
| client\_id | 用户clientId | 字符 | N |
| de | 调用方 | 字符 | N |

> 说明：client\_id即为tmxmall的API Key，client\_id需要登录到Tmxmall网站个人中心查看。

### 返回参数

| 参数名称 | 说明 | 参数类型 | 是否为空 |
| :---: | :---: | :---: | :---: |
| error\_code | 错误码 | 字符 | N |
| error\_msg | 错误信息 | 字符 | N |

> 返回数据为json格式，示例如下：
>
> 成功：{"error\_code":"0","error\_msg":"成功"}
>
> 失败：{"error\_code":"1","error\_msg":"系统异常"}

### 错误码说明

目前可能出现的错误码：

| 错误码 | 错误说明 |
| :--- | :--- |
| TB01002 | 系统错误 |
| TB01001 | 参数不合法\(包括clientId不匹配\) |
| TB01021 | 用户名不存在 |

### 其他异常情况

验证接口超时时间为5秒，5秒无信息返回，软件可认为是Tmxmall网站超时或者是网络超时。



