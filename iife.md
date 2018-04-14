---
description: thử nghiệm
---

# IIFE



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

```text
var myNameSpace = {
	name: null, // khong nen de var o day
	getName: function (name) {
		this.name = name
	},
	hello: function () {
		console.log(this.name); // o 

	},
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

