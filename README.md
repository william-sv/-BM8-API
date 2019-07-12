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
- Type: POST
- Params
```json
{
	"line": "c", // 固定值
	"id": "3770" // 线路名
	"token": "KFJDJJG040F782k="
}
```
- Response
```json
{
	t: 5, //在图中的车辆数
	list: [
		{
			"i": 0,//当前站点序号（0 - n）
			"bl": 3,//正在当前站点的车辆
			"bbl": 0 // 已当前站点已过车辆
		}
	]
}
```
<hr>

##### 获取当前线路 X 站点的车辆情况
- URL: http://gzbus.bm8.com.cn/ajax.php 
- Type: POST 
- Params
```json
{
	"line": "z",
	"id": "333969",
	"token": "GLDLDJI55C5586k="
}
```
- Response
```html
<button  class="am-btn am-btn-primary">1分 2站<br/>粤A22**7D</button><button  class="am-btn am-btn-primary">23分 13站<br/>粤A06**1D</button><button  class="am-btn am-btn-primary">31分 17站<br/>粤A05**9D</button>
```
