# hmac 模块 API 文档

## API

``` python
def new(key:any,msg=None,digestmod="md5")->_hmac.HMAC:...
```



## Examples

### test_hmac.py

```python
import hmac

secret = "0123456789"
payload = "helloworld"

h = hmac.new(secret.encode(),digestmod="md5")
h.update(payload.encode())
print("hmac-md5:",h.hexdigest())

h = hmac.new(secret.encode(),digestmod="sha1")
h.update(payload.encode())
print("hmac-sha1:",h.hexdigest())

h = hmac.new(secret.encode(),digestmod="sha256")
h.update(payload.encode())
print("hmac-sha256:",h.hexdigest())

```
