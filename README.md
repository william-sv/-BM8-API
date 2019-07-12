##### BM8广州公交实时查询 API


##### token 算法
```php
$token_string_1 = 'ABCDEFGHIJKLMN'; // 固定值
$token_string_2 = 'ABCDEFGHIJKLMN0123456789'; // 固定值
$token_string_3 = 'k='; // 固定值
public function getToken($token_value, $length = 7)
{
    $token = '';
    for ($i = 0; $i < $length; $i++){
        $a = floor(lcg_value() * strlen($token_value));
        $token .= substr($token_value, $a, 1);
    }
    return $token;
}
```

<hr>

##### 获取当前线路车辆情况
- URL: http://gzbus.bm8.com.cn/ajax.php
- Method: POST
- Params
```json
{
	"line": "c",
	"id": "3770",
	"token": "KFJDJJG040F782k="
}
```
| 参数  | 值   | 类型   | 释义   |
| ----- | ---- | ------ | ------ |
| line  | c    | String | 固定值 |
| id    |      | String | 线路名 |
| token |      | String | Token  |
- Response
```json
{
    "t": 5, 
    "list": [
        {
	    "i": 0,
	    "bl": 3,
	    "bbl": 0 
	}
    ]
}
```
| Key  | 值   | 类型  | 释义             |
| ---- | ---- | ----- | ---------------- |
| t    |      | int   | 正在途中的车辆数 |
| list |      | Array | 车辆数据         |

###### List内的数据
| Key  | 值   | 类型 | 释义                |
| ---- | ---- | ---- | ------------------- |
| i    |      | int  | 当前站点序号（0-n） |
| bl   |      | int  | 正在当前站点的车辆  |
| bbl  |      | int  | 已当前站点已过车辆  |

<hr>

##### 获取当前线路 X 站点的车辆情况
- URL: http://gzbus.bm8.com.cn/ajax.php 
- Method: POST 
- Params
```json
{
    "line": "z",
    "id": "333969",
    "token": "GLDLDJI55C5586k="
}
```
| 参数  | 值   | 类型   | 释义                     |
| ----- | ---- | ------ | ------------------------ |
| line  | z    | String | 固定值                   |
| id    |      | String | 当前线路中当前站点的编号 |
| token |      | String | Token                    |

- Response
```html
<button  class="am-btn am-btn-primary">1分 2站<br/>粤A22**7D</button><button  class="am-btn am-btn-primary">23分 13站<br/>粤A06**1D</button><button  class="am-btn am-btn-primary">31分 17站<br/>粤A05**9D</button>
```


<hr>


##### 检索线路
- URL: http://gzbus.bm8.com.cn/ajax.php 
- Method: POST 
- Params 
```json
{
    "line": "x",
    "id": "78a",
    "token": "MDNHGMIDBDF7K6k="
}

```
| 参数  | 值   | 类型   | 释义   |
| ----- | ---- | ------ | ------ |
| line  | x    | String | 固定值 |
| id    |      | String | 线路名 |
| token |      | String | Token  |

- Response
```html
<ul class="s_l"><li title='天河智慧城核心区（高唐）总站 => 天河北公交总站'><a href='/line/3770.html'>78A线</a></li></ul>
```
