# requests 模块 API 文档

## API

### class Response(_requests.Response):
``` python
def __init__(self):...
```

``` python
def _append_params_to_url(rqst:Response,url:str,params:dict)->int:...
```

``` python
def _append_headers(rqst:Response,headers:dict)->int:...
```

``` python
def request(method:str,url:str,params=None,headers=None,timeout=0.0,files=None,json=None,data=None)->Response:...
```

初始化请求对象，分配内存和固定请求头 


``` python
def get(url:str,params=None)->Response:...
```



## Examples

### post_data.py

```python
import requests
form_data = '------WebKitFormBoundaryrEPACvZYkAbE4bYB\r\nContent-Disposition: form-data; name="file"; filename="test_file.txt"\r\nContent-Type: text/plain\r\n\r\nhello, pikascript!\r\n------WebKitFormBoundaryrEPACvZYkAbE4bYB\r\nContent-Disposition: form-data; name="id"\r\n\r\n1670666272201\r\n------WebKitFormBoundaryrEPACvZYkAbE4bYB\r\nContent-Disposition: form-data; name="uploadFileNum"\r\n\r\n1\r\n------WebKitFormBoundaryrEPACvZYkAbE4bYB--\r\n'

header = {"Content-Type": "multipart/form-data; boundary=----WebKitFormBoundaryrEPACvZYkAbE4bYB"}

a = requests.request("POST", "http://pikascript.com/upload", headers=header, data=form_data)

print(a.headers)
print(a.content_length)
print(a.text)
```
### get_basic.py

```python
import requests

b = "kkk"

a = requests.request("GET", "http://pikascript.com/package", params = {"name":"get-test"})

print(a.headers)
print(a.content_length)
print(a.text)
```
### requests_encode.py

```python
import requests

a = requests.request("GET", "http://pikascript.com/")

print(a.headers)
print(a.content_length)
print(a.text)


```
### gitee_issue.py

```python

import requests

a = requests.request("GET", "http://pikascript.com/pullrequest", params = {"json":'{"stepIndex":4,"packageName":"None","id":1669300904995,"version":"v1234.4321.1","releases":[],"fileList":[],"userEmail":"test@pikascript.com","userName":"pikascript","pullrequestOK":false,"pullrequestUrl":"","uploadFileNum":1}'})

print(a.headers)
print(a.content_length)
print(a.text)
```
