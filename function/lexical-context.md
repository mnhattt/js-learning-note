

Không giống như các ngôn ngữ khác, quá trình gọi hàm diễn ra tuần tự thì execution context rất dể nắm bắt\(push pop tuần tự\), ở js hàm rất linh động, một hàm con có thể được 1 hàm khác gọi. Do đó nó phải tách ra giữa excution context và lexical enviroments, phân biệt giữa lúc hàm được định nghĩa\(declare\) và lúc được gọi\(invoke\).

Lúc hàm được định nghĩa sẽ có một thuộc tính nội tại là \[\[ Enviroment \]\], chỉ ra môi trường mà nó được định nghĩa\(scope của hàm cao hơn\).

Khi một hàm được gọi, thì sẽ có một execution context\(hàm được gọi từ đâu, hay bởi hàm nào\), một lexical enviroments tương ứng cũng được tạo ra. enviroments này sẽ có một thuộc tính là Outer, Outer sẽ quy chiếu tới thuộc tính \[\[ Enviroment \]\]\(vâng, đã bắt đầu lằng nhằng\).

![](/assets/lexical enviroment.png)  


