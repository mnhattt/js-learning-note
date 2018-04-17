# Object.create

### ongoing lookup-time delegation

tl;dr Object.create sẽ tạo ra 1 obj mới\(rose\) và obj refer tới 1 obj khác\(gold\)

nên khi truy cập thuộc tính mà rose không có\(rose.z\) thì compiler đi tìm tới obj được refer xem nó có thuộc tính đó không  
ở dòng 17 ta thấy gold.z = 3, thì đoán được là rose.z sẽ refer tới đâu ???  
Việc này sẽ giúp giảm được bộ nhớ vì rose không cần phải lưu trữ\(copy\) các thuộc tính/phương thức của đới tượng mà nó được quy chiếu tới.

![](/assets/obj deligate.png)**điều này được áp dụng vào function contructor để tạo ra các đối tượng, mà trong đó các thuộc tính của nó sẽ được refer  tới một đối tượng khác**

### function constructor

còn gọi là decorator pattern

thực chất var obj là closure của hàm Car,  nó sẽ được tạo ra mỗi khi hàm Car được gọi. Do đó mỗi lúc 1 biến cho 1 hàm thì ta sẽ có các obj khác nhau.

được khởi tạo các thuộc tính

```js
var Car = function(loc) {j
  var obj = Obj.create(Car.prototype) (1)
  obj.loc = loc
  return obj
}

Car.prototype.move = function() { this.loc++ }

var amy = Car(1) // tạo clousure
var ben = Car(9) // tạo clousure khác
```

amy và ben đều được trả về là 1 obj nhưng nó hoàn toàn là những Obj khác nhau

### this and new



