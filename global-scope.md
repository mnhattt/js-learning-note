# module pattern

global var có thể được access và thay đổi bởi nhiều thành phần khác, điều này làm chương trình kém bảo mật  và gây ra nhiều lỗi không xác định được, hoặc xung đột tên nếu có nhiều người cũng phát triển

```javascript
var myGlobal = "Look at me";
var useGlobal = function () {
console.log("I can see the global: " + myGlobal);
};
console.log("I too can see the global: " + myGlobal);
```

## giải pháp

1. tập hợp những thuộc tính và hàm liên quan vào trong 1 đối tượng được gọi là namespace

```text
var myNamespace = {
    key: value,
    methode1: function () {
    }  
}
```

2.  Bao lại bằng hàm để tạo local scope

```javascript
var myGlobal = function () {
    var mylocal
    
    var getLocal = function () { return myLocal }
    var setLocal = function (para) { myLocal = para }
    
    return {  
        getLocal:  getLocal,
        setLocal:  setLocal
    }
}

// đây chính là module pattern trong JS !
```

