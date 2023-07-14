# json 模块 API 文档

## API

``` python
def loads(json:str)->dict:...
```

``` python
def dumps(d:dict)->str:...
```



## Examples

### json_dumps.py

```python
import json

s0 = json.dumps(1)

s1 = json.dumps({"a": 1, "b": 2, "c": 3})
print(s1)

s2 = json.dumps(
    {
        "a": 1,
        "b": 2,
        "c": 3,
        "d": {
            "e": 4,
            "f": 5
        }
    }
)
print(s2)

s3 = json.dumps(
    {
        "a": 1,
        "b": 2,
        "c": 3,
        "d": {
            "e": 4,
            "f": 5
        },
        "g": [
            6,
            7,
            8
        ]
    }
)
print(s3)

s4 = json.dumps(
    {
        "a": 1,
        "b": 2,
        "c": 3,
        "d": {
            "e": 4,
            "f": 5
        },
        "g": [
            6,
            7,
            8
        ],
        "h": None,
        "i": False,
        "j": True,
        "k": "string",
        "l": 1.234
    }
)
print(s4)

```
### json_loads.py

```python
import json
import time

res = json.loads('{"a": 1, "b": 2, "c": 3}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3

res = json.loads('{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8]}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false, "j": true}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false, "j": true, "k": "string"}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True
assert res['k'] == 'string'

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false, "j": true, "k": "string", "l": 1.234}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True
assert res['k'] == 'string'
assert res['l'] == 1.234


# Testing empty object and empty array using type and len
res = json.loads('{}')
assert type(res) == dict
assert len(res) == 0

res = json.loads('[]')
assert type(res) == list
assert len(res) == 0

res = json.loads('{"a": {}}')
assert type(res['a']) == dict
assert len(res['a']) == 0

res = json.loads('{"a": []}')
assert type(res['a']) == list
assert len(res['a']) == 0

res = json.loads('{"a": 1, "b": {}, "c": []}')
assert res['a'] == 1
assert type(res['b']) == dict
assert len(res['b']) == 0
assert type(res['c']) == list
assert len(res['c']) == 0

res = json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": {}}, "g": [6, {}, 8], "h": null, "i": false, "j": true, "k": "string", "l": 1.234}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert type(res['d']['f']) == dict
assert len(res['d']['f']) == 0
assert res['g'][0] == 6
assert type(res['g'][1]) == dict
assert len(res['g'][1]) == 0
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True
assert res['k'] == 'string'
assert res['l'] == 1.234
print('PASS')

```
### json_err.py

```python
import json
# test parse failure

try:
    json.loads('{')
except:
    print('FAIL')

try:
    json.loads('{"a":1,}')
except:
    print('FAIL')

try:
    json.loads('{"a":1,')
except:
    print('FAIL')

try:
    json.loads('{"a":1, "b":}')
except:
    print('FAIL')

try:
    json.loads('{"a":1, "b":, "c":3}')
except:
    print('FAIL')

try:
    json.loads('{"a":1 "b":2}')
except:
    print('FAIL')

try:
    json.loads('{"a":1, "b":2, "c":3,}')
except:
    print('FAIL')

try:
    json.loads('{"a":1, "b"2, "c":3}')
except:
    print('FAIL')

```
### json_issue1.py

```python
import json
data = '{"code": 0,"path": "act_mode_config", "act_mode": [["ACTUATOR_NAME","ACTUATOR_ID","ACTUATOR_MODE_NAME","ACTUATOR_MODE_ID","ACT_MODE_TYPE","ACT_VALUE_TIME_s"],["电机1","actuator123","开闭循环1","mode2345","loop","{\\"AC_VALUE\\":1,\\"ACT_TIME_s\\":300}"],["电机1","actuator123","常开","mode2346","always","{\\"AC_VALUE\\":1,\\"ACT_TIME_s\\"}:0"]],"ext": "data"}'

print(data)
json_data = json.loads(data)
ACT_VALUE_TIMS_S = json_data['act_mode'][1][5]
print(ACT_VALUE_TIMS_S)
act_value_tims_json = json.loads(ACT_VALUE_TIMS_S)
print(act_value_tims_json['ACT_TIME_s'])
act_time_s = act_value_tims_json['ACT_TIME_s']

```
### json_speed.py

```python
import json
import time

dict_test = {'widget0': {"type": "div", "attributes": {"class": "container", "style": {"width": 240, "height": 240, "margin": 0, "padding": 0, "border-radius": 0, "border-width": 0, "border-color": "red", "background-color": 37864}}, "nodes": [{"type": "text", "attributes": {"font-size": "30", "class": "result-text", "style": {"top": 5, "left": 5, "width": 220, "text-align": "right", "height": 30, "color": "white", "text-overflow": "longbreak", "border-width": 0, "border-color": "red", "background-color": "transparent"}}, "nodes": [], "bindings":[{"attrName": "text", "key": "result", "isText": True}], "events": [], "value":"0", "widgetName":"widget1"}, {"type": "div", "attributes": {"class": "key-wrapper", "onclick": "onclick", "style": {"width": 60, "height": 50, "border-width": 0, "border-color": "red", "background-color": "transparent", "top": 40, "left": 10}}, "nodes": [{"type": "text", "attributes": {"font-size": "30", "class": "key", "style": {"left": 0, "top": 0, "width": 50, "height": 40, "margin": 0, "padding": 0, "color": "white", "font-size": 30, "text-align": "center", "background-color": "transparent"}}, "nodes": [], "bindings":[], "events":[], "value":"1", "widgetName":"widget3"}], "bindings":[], "events":[{"onclick": "onclick"}], "widgetName": "widget2"}, {"type": "div", "attributes": {"class": "key-wrapper", "onclick": "onclick", "style": {"width": 60, "height": 50, "border-width": 0, "border-color": "red", "background-color": "transparent", "top": 40, "left": 60}}, "nodes": [{"type": "text", "attributes": {"font-size": "30", "class": "key", "style": {
    "left": 0, "top": 0, "width": 50, "height": 40, "margin": 0, "padding": 0, "color": "white", "font-size": 30, "text-align": "center", "background-color": "transparent"}}, "nodes": [], "bindings":[], "events":[], "value":"2", "widgetName":"widget5"}], "bindings":[], "events":[{"onclick": "onclick"}], "widgetName": "widget4"}, {"type": "div", "attributes": {"class": "key-wrapper", "onclick": "onclick", "style": {"width": 60, "height": 50, "border-width": 0, "border-color": "red", "background-color": "transparent", "top": 40, "left": 110}}, "nodes": [{"type": "text", "attributes": {"font-size": "30", "class": "key", "style": {"left": 0, "top": 0, "width": 50, "height": 40, "margin": 0, "padding": 0, "color": "white", "font-size": 30, "text-align": "center", "background-color": "transparent"}}, "nodes": [], "bindings":[], "events":[], "value":"3", "widgetName":"widget7"}], "bindings":[], "events":[{"onclick": "onclick"}], "widgetName": "widget6"}, {"type": "div", "attributes": {"class": "key-wrapper", "onclick": "onclick", "style": {"width": 60, "height": 50, "border-width": 0, "border-color": "red", "background-color": "transparent", "top": 40, "left": 160}}, "nodes": [{"type": "text", "attributes": {"font-size": "30", "class": "key", "style": {"left": 0, "top": 0, "width": 50, "height": 40, "margin": 0, "padding": 0, "color": "white", "font-size": 30, "text-align": "center", "background-color": "transparent"}}, "nodes": [], "bindings":[], "events":[], "value":"+", "widgetName":"widget9"}], "bindings":[], "events":[{"onclick": "onclick"}], "widgetName": "widget8"}], "bindings": [], "events": [], "widgetName": "widget0"}}

json.CONFIG_USING_CJSON = True
print('dict_test:', dict_test)
json_test = json.dumps(dict_test)
print('json_test:', json_test)

json.CONFIG_USING_CJSON = True
start = time.tick_ms()
for i in range(10):
    res = json.loads(json_test)
str_res_cjson = str(res)
print('len(str_res_cjson):', len(str_res_cjson))
end = time.tick_ms()
time_cjson_loads = end - start
print('loads: cjson:', time_cjson_loads, 'ms')

json.CONFIG_USING_CJSON = False
start = time.tick_ms()
for i in range(10):
    res = json.loads(json_test)
str_res_jsmn = str(res)
print('len(str_res_jsmn):', len(str_res_jsmn))
end = time.tick_ms()
time_jsmn_loads = end - start

print('loads: jsmn:', time_jsmn_loads, 'ms')

# test for dumps

# test for dumps

json.CONFIG_USING_CJSON = True
start = time.tick_ms()
for i in range(10):
    res = json.dumps(dict_test)
len_res_cjson = len(res)
print('len(res_cjson):', len_res_cjson)
end = time.tick_ms()
time_cjson_dumps = end - start
print('dumps: cjson:', time_cjson_dumps, 'ms')

json.CONFIG_USING_CJSON = False
start = time.tick_ms()
for i in range(10):
    res = json.dumps(dict_test)
len_res_jsmn = len(res)
print('len(res_jsmn):', len_res_jsmn)
end = time.tick_ms()
time_jsmn_dumps = end - start
print('dumps: jsmn:', time_jsmn_dumps, 'ms')

print('==================================================')
print('loads: jsmn is', (time_cjson_loads /
      time_jsmn_loads), 'times faster than cjson')
print('dumps: jsmn is', (time_cjson_dumps /
      time_jsmn_dumps), 'times faster than cjson')

```
### _json_loads.py

```python
import _json

res = _json.loads('{"a": 1, "b": 2, "c": 3}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3

res = _json.loads('{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5

res = _json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8]}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8

res = _json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None

res = _json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False

res = _json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false, "j": true}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True

res = _json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false, "j": true, "k": "string"}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True
assert res['k'] == 'string'

res = _json.loads(
    '{"a": 1, "b": 2, "c": 3, "d": {"e": 4, "f": 5}, "g": [6, 7, 8], "h": null, "i": false, "j": true, "k": "string", "l": 1.234}')
assert res['a'] == 1
assert res['b'] == 2
assert res['c'] == 3
assert res['d']['e'] == 4
assert res['d']['f'] == 5
assert res['g'][0] == 6
assert res['g'][1] == 7
assert res['g'][2] == 8
assert res['h'] is None
assert res['i'] is False
assert res['j'] is True
assert res['k'] == 'string'
assert res['l'] == 1.234
print('PASS')

```
