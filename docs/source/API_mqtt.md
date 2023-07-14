# mqtt 模块 API 文档

## API

### class MQTT(_mqtt._MQTT):
``` python
def __init__(self,ip:str,port=1883,clinetID='mac',username='',password='',version='3.1.1',ca='',keepalive=60):...
```

``` python
def subscribe(self,topic,cb,qos=1):...
```

``` python
def publish(self,topic,payload,qos=1):...
```

``` python
def setWill(self,topic,payload,qos=1,retain=0):...
```

``` python
def unsubscribe(self,topic=''):...
```



## Examples

### mqtt_subscribe.py

```python
import mqtt
import PikaStdDevice

client = mqtt.MQTT('broker.emqx.io', port=1883,
                   clinetID='clientid', username='name_', password='passwd_')

ret = client.connect()
print("connect ret:%d" % ret)


def callback0(evt):
    print("py0 cb: %s-qos:%d-->>%s" % (evt.topic, evt.qos, evt.msg))


def callback1(evt):
    print("py1 cb: %s-qos:%d-->>%s" % (evt.topic, evt.qos, evt.msg))


def callback2(evt):
    print("py2 cb: %s-qos:%d-->>%s" % (evt.topic, evt.qos, evt.msg))


def reconnect_mq(signal):
    print('lost mqtt connect and try to reconnect')
    print('signal:', signal)


client.setKeepAlive(5)
ret = client.subscribe('topic_pikapy_qos0', callback0, 0)
print("subscribe ret:%d" % ret)
ret = client.subscribe('topic_pikapy_qos1', callback1, 1)
print("subscribe ret:%d" % ret)
ret = client.subscribe('topic_pikapy_qos2', callback2, 2)
print("subscribe ret:%d" % ret)

client._fakeMsg("topic_pikapy_qos0", 0, "hello qos0")
client._fakeMsg("topic_pikapy_qos1", 1, "hello qos1")
client._fakeMsg("topic_pikapy_qos2", 2, "hello qos2")

# sleep wait for recv data
T = PikaStdDevice.Time()
# T.sleep_s(5)

out = client.listSubscribeTopic()
print('listSubscribeTopic out', out)

# client.unsubscribe('topic_pikapy_qos0');
# client.unsubscribe('topic_pikapy_qos1');
# client.unsubscribe('topic_pikapy_qos2');
# T.sleep_s(5)
# out2 = client.listSubscribeTopic()
# print('listSubscribeTopic out2',out2)

ret = client.setDisconnectHandler(reconnect_mq)
print("setDisconnectHandler:%d" % ret)

# ret = client.setWill('topic_will','lost mqtt connect')
# print("setWill:%d" % ret)
# client.publish('topic_will', 'hello pikascript', 1)
# T.sleep_s(5)
# print("sleep_s:5s")

# T.sleep_s(30)
# exit()
ret = client.disconnect()
print("disconnect ret:%d" % ret)

```
### mqtt_connect.py

```python
import mqtt

client = mqtt.MQTT('broker.emqx.io',port=1883,clinetID='clientid',username='name_',password='passwd_')

ret = client.connect()
print("connect ret:%d" % ret)

ret = client.disconnect()
print("disconnect ret:%d" % ret)

```
### mqtt_init.py

```python
import mqtt

client = mqtt.MQTT('broker.emqx.io')




```
### mqtt_set_para.py

```python
import mqtt

test_baidu_ca_crt = ["-----BEGIN CERTIFICATE-----\r\n"
    "MIIDXzCCAkegAwIBAgILBAAAAAABIVhTCKIwDQYJKoZIhvcNAQELBQAwTDEgMB4G\r\n"
    "A1UECxMXR2xvYmFsU2lnbiBSb290IENBIC0gUjMxEzARBgNVBAoTCkdsb2JhbFNp\r\n"
    "Z24xEzARBgNVBAMTCkdsb2JhbFNpZ24wHhcNMDkwMzE4MTAwMDAwWhcNMjkwMzE4\r\n"
    "MTAwMDAwWjBMMSAwHgYDVQQLExdHbG9iYWxTaWduIFJvb3QgQ0EgLSBSMzETMBEG\r\n"
    "A1UEChMKR2xvYmFsU2lnbjETMBEGA1UEAxMKR2xvYmFsU2lnbjCCASIwDQYJKoZI\r\n"
    "hvcNAQEBBQADggEPADCCAQoCggEBAMwldpB5BngiFvXAg7aEyiie/QV2EcWtiHL8\r\n"
    "RgJDx7KKnQRfJMsuS+FggkbhUqsMgUdwbN1k0ev1LKMPgj0MK66X17YUhhB5uzsT\r\n"
    "gHeMCOFJ0mpiLx9e+pZo34knlTifBtc+ycsmWQ1z3rDI6SYOgxXG71uL0gRgykmm\r\n"
    "KPZpO/bLyCiR5Z2KYVc3rHQU3HTgOu5yLy6c+9C7v/U9AOEGM+iCK65TpjoWc4zd\r\n"
    "QQ4gOsC0p6Hpsk+QLjJg6VfLuQSSaGjlOCZgdbKfd/+RFO+uIEn8rUAVSNECMWEZ\r\n"
    "XriX7613t2Saer9fwRPvm2L7DWzgVGkWqQPabumDk3F2xmmFghcCAwEAAaNCMEAw\r\n"
    "DgYDVR0PAQH/BAQDAgEGMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYEFI/wS3+o\r\n"
    "LkUkrk1Q+mOai97i3Ru8MA0GCSqGSIb3DQEBCwUAA4IBAQBLQNvAUKr+yAzv95ZU\r\n"
    "RUm7lgAJQayzE4aGKAczymvmdLm6AC2upArT9fHxD4q/c2dKg8dEe3jgr25sbwMp\r\n"
    "jjM5RcOO5LlXbKr8EpbsU8Yt5CRsuZRj+9xTaGdWPoO4zzUhw8lo/s7awlOqzJCK\r\n"
    "6fBdRoyV3XpYKBovHd7NADdBj+1EbddTKJd+82cEHhXXipa0095MJ6RMG3NzdvQX\r\n"
    "mcIfeg7jLQitChws/zyrVQ4PkX4268NXSb7hLi18YIvDQVETI53O9zJrlAGomecs\r\n"
    "Mx86OyXShkDOOyyGeMlhLxS67ttVb9+E7gUJTb0o2HLO02JQZR7rkpeDMdmztcpH\r\n"
    "WD9f\r\n"
    "-----END CERTIFICATE-----"]

client = mqtt.MQTT('192.168.1.255')

#test TLS
# client.setHost('j6npr4w.mqtt.iot.gz.baidubce.com')
# client.setPort(1884)
# client.setCa(test_baidu_ca_crt)

client.setHost('broker.emqx.io')
client.setPort(1883)

client.setClientID('123456dddecetdc')
client.setUsername('j6npr4w/mqtt-client-dev')
client.setPassword('lcUhUs5VYLMSbrnB')
client.setVersion('3.1.1')
client.setKeepAlive(10)

ret = client.connect()
print("connect ret:%d" % ret)

ret = client.disconnect()
print("disconnect ret:%d" % ret)
```
### mqtt_publish.py

```python
import mqtt

client = mqtt.MQTT('192.168.1.255')

client.setHost('broker.emqx.io')
client.setPort(1883)
client.setClientID('123456dddecetdc')
client.setUsername('test1')
client.setPassword('aabbccdd')
client.setVersion('3.1')
client.setKeepAlive(10)

ret = client.connect()
print("connect ret:%d" % ret)

client.publish('topic_pikapy', 'hello pikascript qos=0', 0)
client.publish('topic_pikapy', 'hello pikascript qos=1', 1)
client.publish('topic_pikapy', 'hello pikascript qos=2', 2)

ret = client.disconnect()
print("disconnect ret:%d" % ret)

```
