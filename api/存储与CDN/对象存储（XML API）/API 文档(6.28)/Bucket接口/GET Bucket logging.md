## 功能描述
获取存储桶 logging 配置信息。

## 请求

### 请求示例
```
GET /?logging HTTP 1.1
Host: <Bucketname-APPID>.cos.<Region>.myqcloud.com
Date: GMT Date
Authorization: Auth String
```

> Authorization: Auth String (详细参见 [请求签名](https://cloud.tencent.com/document/product/436/7778) 章节)

### 请求行
~~~
GET /?cors HTTP/1.1
~~~
该 API 接口接受 GET 请求。

### 请求头
#### 公共头部
该请求操作的实现使用公共请求头，了解公共请求头详细请参见 [公共请求头部](https://cloud.tencent.com/document/product/436/7728) 章节。
#### 非公共头部
该请求操作无特殊的请求头部信息。
### 请求体
该请求的请求体为空。

## 响应

### 响应头
#### 公共响应头 
该响应使用公共响应头，了解公共响应头详细请参见 [公共响应头部](https://cloud.tencent.com/document/product/436/7729) 章节。
#### 特有响应头
该响应无特殊的响应头。
### 响应体
该响应体返回为 **application/xml** 数据，包含完整节点数据的内容展示如下：
```
<BucketLoggingStatus>
  <LoggingEnabled>
    <TargetBucket></TargetBucket>
    <TargetPrefix></TargetPrefix>
  </LoggingEnabled>
</BucketLoggingStatus>
```
具体的数据内容如下：<style  rel="stylesheet"> table th:nth-of-type(1) { width: 200px; }</style>

|节点名称（关键字）|父节点|描述|类型|
|:---|:-- |:--|:--|
| BucketLoggingStatus |无| 存储桶日志状态信息 | Container |

Container 节点 BucketLoggingStatus 的内容：

|节点名称（关键字）|父节点|描述|类型|
|:---|:-- |:--|:--|
| LoggingEnabled | BucketLoggingStatus | 存储桶日志记录配置详细信息 |  Container |

Container 节点 LoggingEnabled 的内容：

|节点名称（关键字）|父节点|描述|类型|
|:---|:-- |:--|:--|
| TargetBucket | LoggingEnabled | 日志存储的目标 Bucket，既可以为相同 Bucket，也可以相同账户下相同地域的 Bucket  |  String |
| TargetPrefix | LoggingEnabled | 日志存储的目标 Bucket 指定路径 |  String |

## 实际案例

### 请求
```
GET /?logging HTTP 1.1
Host: mybucket-1258888888.cos.ap-beijing.myqcloud.com
Date: Wed, 28 Oct 2017 21:32:00 GMT
Authorization: q-sign-algorithm=sha1&q-ak=AKIDWtTCBYjM5OwLB9CAwA1Qb2ThTSUjfABC&q-sign-time=1484815944;32557711944&q-key-time=1484815944;32557711944&q-header-list=host&q-url-param-list=accelerate&q-signature=a2d28e1b9023d09f9277982775a4b3b705d0e23e
```

### 响应
```
HTTP/1.1 200 OK
Content-Type: application/xml
Content-Length: 142
Connection: keep-alive
Date: Wed, 28 Oct 2017 21:32:00 GMT
Server: tencent-cos
x-cos-request-id: NTg4MDdlNGZfNDYyMDRlXzM0YWFfZT==

<BucketLoggingStatus>
  <LoggingEnabled>
    <TargetBucket>logs</TargetBucket>
    <TargetPrefix>logdir</TargetPrefix>
  </LoggingEnabled>
</BucketLoggingStatus>
```

