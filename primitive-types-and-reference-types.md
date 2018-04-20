## Bản chất của biến

biến là một địa chỉ\(trong không gian nhớ\) lưu giá trị nhị phân nào đó

vì làm việc với địa chỉ bộ nhớ quá phức tạp nên ta sẽ tạo ra khái niệm biến

var a = true

là ta sẽ tạo trong bộ nhớ 1 block mới\(giả sử 0x60\) và gán cho nó giá trị 0x01

từ giờ sẽ không làm việc với các địa chỉ 0xxxx rất khó nhớ nữa mà làm việc với các biến có tên dể nhớ hơn như a

## ![](/assets/data-type-1.png)

## Primitive types and Reference types

với việc đọc/hiểu biến theo 2 cách đó ta có 2 loại giá trị tương ứng primitive values và reference  values

với primitive values

với reference  values

Trong js để tạo ra một đối tượng mới thì chỉ có 2 cách

dùng constructor hoặc là literal methode

```
var obj = {}
var obj = new Object()

tương đương, cấp phát, tạo 1 đối tượng trong bộ nhớ 
trả địa chỉ của đối tượng đó về cho biến obj
```

## Array, Function, ...

là các loại reference  values khác

Tương tự Object, khi tạo một function là ta đã tạo ra một đối tượng function\(ở đâu đó trong bộ nhớ\). 2 tạo bằng declare và expression thật chất đề là gán địa chỉ của func obj đó cho biến func\_obj

```
var func_obj = function () {
    // đối tượng anonymous function sẽ được tạo ra
    // địa chỉ đối tượng được trả về cho func_obj 
}

var another_func_obj = func_obj

another_func_obj và func_obj sẽ điều chỉ tới 1 đối tượng anonymous function
```

tương đương

```
function anonymous() = {}

var func_obj = anonymous
var another_func_obj = anonymous
```

vấn đề trở nên dể nhầm lẫn vì chúng ta có quá nhiều anonymous function được tạo ra

```
var func_obj = function () { }
var another_func_obj = function () { }

console.log(func_obj === another_func_obj) // false
```



