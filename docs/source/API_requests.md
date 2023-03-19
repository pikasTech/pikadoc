# requests 模块 API 文档

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

