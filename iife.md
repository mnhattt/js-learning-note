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

