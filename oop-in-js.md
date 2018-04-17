# Object.create

### ongoing lookup-time delegation

tl;dr Object.create sẽ tạo ra 1 obj mới\(rose\) và obj refer tới 1 obj\(gold\) khác

### ![](/assets/obj deligate.png)function constructor

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





