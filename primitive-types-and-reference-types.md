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

var obj = {}

var obj new Object\(\)

tương đương, cấp phát 1 vùng nhớ trong bộ nhớ cho biến obj

## Array, Function, ...

là các loại reference  values khác

