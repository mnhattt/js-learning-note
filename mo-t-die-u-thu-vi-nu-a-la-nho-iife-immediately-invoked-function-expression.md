---
description: vài thử nghiệm
---

# Một điều thú vị nữa là nhờ IIFE \(Immediately Invoked Function Expression\)

## Không dùng IIFE

```javascript
var myNameSpace = { name: null, // khong nen de var o day getName: function (name) { this.name = name }, hello: function () { console.log(this.name); // o
 }, local: (function () { var local = null return { getLocal: (function () { return local })(), setLocal: (function (params) { local = params })() } })()}
```

