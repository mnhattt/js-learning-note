# IIFE

## Không dùng IIFE

```javascript
var Global = {
	local: function () {
		var local = null
		return {
			getLocal: function () {
				return local
			},
			setLocal: function (params) {
				local = params
			}
		}
	}
}

// console.log( Global.local().getLocal())
```

## Dùng IIFE

```javascript
var Global= {
	local: (function () {
		var local = null
		return {
			getLocal: (function () {
				return local
			})(),
			setLocal: function (params) {
				local = params
			}
		}
	})()
}

// not work !!! 
// console.log( Global.local.getLocal) => null
//  Global.local.setLocal('123')
// console.log( Global.local.getLocal) => null
```

### vấn đề là chổ getLocal và setLocal invoke 2 hàm khác nhau và do đó closure\(var local\) sẽ khác nhau

```javascript
var Global= {
	local: (function () {
		var local = null
		return {
			getLocal: function () {
				return local
			},
			setLocal: function (params) {
				local = params
			}
		}
	})()
}

// bo IIFE chổ setLocal đi, cả 2 sẽ cùng chung 1 closure
// it work !
 Global.local.setLocal('namespace')
console.log( Global.local.getLocal());
```



Như trường hợp này khi in ra thì message dã undifine

![](https://scontent.fdad3-1.fna.fbcdn.net/v/t1.0-9/30714078_1837378226293959_5390352787974136281_n.png?_nc_cat=0&oh=ee1021bbf2bd3a69008622a139742593&oe=5B28BD57)

một ví dụ khác [ở đây](https://medium.com/@vnknowledge/javascript-c%C4%83n-b%E1%BA%A3n-gi%E1%BB%9Bi-thi%E1%BB%87u-v%E1%BB%81-bi%E1%BB%83u-th%E1%BB%A9c-iife-606c4567e7ec). Mối hàm  result\(\) sẽ truy cập tới 1 closure khác nhau

```text
var result = [];
for(var year = 0; year < 5; year++) {
    (function() {
        var y = year;
        result.push(function() { return y; });
    })();
}
console.log(result[1]()); // 1
console.log(result[3]()); // 3
```



