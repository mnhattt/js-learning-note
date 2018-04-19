first class citizen

scope/clousure\(excution context\)

this\(function context\)

lexical enviroment

excution context chính là các callstack =&gt; ý nghĩa là biến local của stack ở dưới \(cha/hàm gọi caller\) có thể pass vào stack ở trên \(con/ hàm được gọi callee\) 

Vì JS là single thread nên nó thực hiện tuần tự, chúng ta cần track được là nó thực hiện đến đâu

thử nghiệm: tạo một hàm con trong một hàm cha\(1\), hàm con đó được gọi bởi hàm\(2\) =&gt; Không ổn

```
function Cha(test) {  (1)
    function Con(test) {  (2)
        console.log(test);
    }
    Con(test) (2) 
    
    function Test() {
        console.log(test);
    }
    Test() // vẫn ok nhờ clousre
}
Cha('234') (1)
```

Khi hàm con\(\) được gọi thì sẽ có local chính là test \(2\), test \(1\) là local của Cha nên sẽ là clousure của Con

1 hàm chỉ 

