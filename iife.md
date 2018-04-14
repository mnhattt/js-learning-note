---
description: thử nghiệm
---

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

![](https://scontent.fdad3-1.fna.fbcdn.net/v/t1.0-9/30714078_1837378226293959_5390352787974136281_n.png?_nc_cat=0&oh=ee1021bbf2bd3a69008622a139742593&oe=5B28BD57)



