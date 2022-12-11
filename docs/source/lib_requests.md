#### request模块说明

Author: Onceday	Date: 2022年12月10日

##### 1. 模块基本情况

1. 基于webclient.c开发，暂时支持最简单的get请求和post请求。
2. 在get请求上额外支持简单的拼接URL。
3. 能够指定额外的请求头关键字。
4. 返回数据包括状态码，负载内容长度，和负载内容。

##### 2. 使用方法

1. 首先导入模块

   ```yacas
   import request
   ```

2. 然后输入方法和url地址

   ```yacas
   result = requests.request("GET", "http://pikascript.com/")
   ```

3. 如果一切成功，result中将含有以下信息

   ```yacas
   content_length: int		返回文本内容的长度
   text: str				返回的文本内容
   state_code: int			get请求的状态码
   headers: str			返回的响应头
   url: str				get请求的url地址
   ```

   其中，text是最核心的返回数据。

   对于(2)中的请求，可以如下展示：

   ```yacas
   print(result.text)
   ```

   这就是网页`http://pikascript.com/`的内容了。

4. 如果这个`request`失败，那么result会是一个空对象，因此需要判断result是否为空。

`request`模块目前可用参数有如下几种：

```yacas
request(method: str, url: str, params=None, headers=None, data=None) -> Response:
```

- `method`, 可选`GET`、`POST`，最基本的两种操作
- `url`,  即标准的url字段，注意有长度限制，最好不要超过2Kb。
- `params`，可选，用于在已给的url字段后面拼接参数，会自动转义字符，也可以在url中手动拼接。
- `headers`，可选，用于指定请求头的关键字，如`Host`等，用于满足自定义的需求，正常使用无需填写。
- `data`，用于在`POST`中传输的负载数据，注意是字符串类型。
- `Response`，返回的响应对象，只有发送的请求响应成功，才会返回，否则为`None`。

##### 3.  拼接 URL

get方法额外支持的就是拼接URL，这个过程也会涉及一些字符的转换。因为URL里面有一些特殊字符是不能直接展示的，必须转义才行。

使用很简单，如下：

```yacas
result = requests.request("GET", "http://pikascript.com/package", params = {"name":"get-test", "id":"23"})
```

其中，url会拼接成如下：

```yacas
http://pikascript.com/package?name=get-test&id=23
```

然后便以此来发送`http`请求，这里并没有做很复杂的操作，只是简单的把字典里面的参数连接起来。

然后如下来显示返回的数据，只有成功收到响应result才不为空，所以要判断一下：

```yacas
if result not None:
	print(result.status_code)
	print(result.content_length)
	print(result.text)
```

##### 4. post接口

该接口比较原始，如果想自己上传数据，则需要手动拼接内容。原因如下：

1. http协议非常复杂，没有必要重复实现一遍。
2. 嵌入式的需求是固定的。

下面是一个典型的使用：

```yacas
import requests
print("test")
form_data = '------WebKitFormBoundaryrEPACvZYkAbE4bYB\r\nContent-Disposition: form-data; name="file"; filename="test_file.txt"\r\nContent-Type: text/plain\r\n\r\nhello, pikascript!\r\n------WebKitFormBoundaryrEPACvZYkAbE4bYB\r\nContent-Disposition: form-data; name="id"\r\n\r\n1670666272201\r\n------WebKitFormBoundaryrEPACvZYkAbE4bYB\r\nContent-Disposition: form-data; name="uploadFileNum"\r\n\r\n1\r\n------WebKitFormBoundaryrEPACvZYkAbE4bYB--\r\n'

print(form_data)
header = {"Content-Type": "multipart/form-data; boundary=----WebKitFormBoundaryrEPACvZYkAbE4bYB"}

a = requests.request("POST", "http://pikascript.com/upload", headers=header, data=form_data)

if a not None:
	print(a.headers)
	print(a.content_length)
	print(a.text)
```

正常输出如下：

```yacas
HTTP/1.1 200 OK
309
{"files":{"file":[{"fieldName":"file","originalFilename":"test_file.txt","path":"html/upload/pJwNgC8fobWOLN_l9qmAk-Oi.txt","headers":{"content-disposition":"form-data; name=\"file\"; filename=\"test_file.txt\"","content-type":"text/plain"},"size":18}]},"fields":{"id":["1670666272201"],"uploadFileNum":["1"]}}
```

下面来解释一下上面的行为：

1. 首先指定额外的请求头关键字，`Content-Type`表明负载的类型，`multipart/form-data`是一种常见的表单类型，`boundary`指定表单不同部分之间的分割线。

   ```
   Content-Type:multipart/form-data; boundary=----WebKitFormBoundaryrEPACvZYkAbE4bYB
   ```

   `----WebKitFormBoundaryrEPACvZYkAbE4bYB`就是用来分割负载内容的，这只是单纯的一些随机字符，所以可以参杂一些标识`WebKitFormBoundaryr`在里面。

   你会发现，这个分隔符可能和传输的内容重复！对的，可能重复，重复就会导致服务器解析失败，然后需要再传一次。因此每次都是随机的字符串，连续多次重复的概率是非常低的。

   上面表单数据即编码后的字符串，其含有三种数据:

   	1. 文件名、文件类型和文件的内容"hello, pikascript!"。
   	1. 对应ID。
   	1. 上传文件的数目。

2. POST关键需要以下两个请求关键字：

   ```yacas
   header buffer:POST http://pikascript.com/upload HTTP/1.1
   Content-Type:multipart/form-data; boundary=----WebKitFormBoundaryrEPACvZYkAbE4bYB
   Content-Length: 408
   ```

   对于一个post来说，其请求头最简单时只需要如上内容即可。

3. 返回码可以看到为200，这表示post请求成功了，当然，这个post响应还携带一些关于上传内容的信息。

**最直接的post传输，只需要如下调用即可**。

```yacas
a = requests.request("POST", "http://pikascript.com/upload", data=binary_data)
```

这个传输的是二进制数据，即默认填充以下内容：

```yacas
Content-Type: application/octet-stream
Content-Length: (sizeof(data))
```

但这需要服务器对应支持解析，很明显，`http://pikascript.com/upload`不能解析这种数据。

##### 5. 运行过程

整个request代码是基于webclient开发，并进行了简单的更改。

当运行如下语句时，实际进行了下列过程：

```yacas
result = requests.request("GET", "http://pikascript.com/package", params = {"name":"get-test"}, headers = {"Connection":"keep-alive"})
```

- 首先创建一个session对象，申请4Kb buffer空间存放请求头。
- 写入`GET`到buffer中。
- 写入"http://pikascript.com/package"到buffer中，
- 写入url的拼接部分`params = {"name":"get-test"}`到buffer中，然后补充必要的其他字符。
- 写入指定的关键字`headers = {"Connection":"keep-alive"}`到buffer中。
- 对于POST，会额外写入`Content-Type`和`Content-Length`内容。
- **这里会开始解析URL地址，比如将域名解析为实际的IP地址**。
- 写入默认的标准头部分关键字，包括
  1. `Host: (自行解析)`
  2. `User-Agent: PikaScript HTTP Agent`
  3. `Accept: */*`
- **创建socket连接，开始通信**。
- 先发送请求头部分数据，再发送数据(对于POST)。
- 然后是等待接收数据了，这个时候有超时的可能。
- 解析数据，写入content_length、text、header、status_code这四个内容。

最后可通过返回的result对象查看上面四个数据。
