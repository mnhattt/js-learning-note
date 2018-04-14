---
description: thử nghiệm
---

# IIFE

Khong dung IIFE

```javascript
var myNameSpace = {
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

// console.log(myNameSpace.local().getLocal())
```

Dung IIFE

```javascript
var myNameSpace = {
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
// console.log(myNameSpace.local.getLocal) => null
// myNameSpace.local.setLocal('123')
// console.log(myNameSpace.local.getLocal) => null
```

### vấn đề là chổ getLocal và setLocal invoke 2 hàm khác nhau và do đó closure\(var local\) sẽ khác nhau

```javascript
var myNameSpace = {
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
myNameSpace.local.setLocal('namespace')
console.log(myNameSpace.local.getLocal());
```

