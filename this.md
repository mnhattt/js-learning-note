Khi một hàm được thực thi\(hay được gọi\) thì luôn có một ngữ cảnh\(excution context\) để hàm đó thực thi.  Ngữ cảnh đó chính là **this**. Muốn xác định this thì luôn phải đặt câu hỏi, ngữ cảnh mà hàm đó đang thực thi là gì

```
// 'use strict';

var Func = function () {
    console.log(this);
}

Func()
new Func()
```

Khi hàm được gọi thẳng mà không thông qua bất cứ obj nào thì bối cảnh của nó sẽ là global hoặc undifine\(nếu dùng 'use strict';\)

```
var Func = function () {
    this.abc = 'xyz'
    this.log = function () {
        console.log(this);
    }
}
var func = new Func()
func.log()

var Func = {
    abc: 'xyz',
    log : function () {
        console.log(this);
    }
}
Func.log()
```



