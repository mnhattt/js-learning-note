# func constructor vs obj constructor

## Vấn đề

Viết một chương trình làm quiz

> &gt; quiz.quizMe\(\)  
> What is the highest mountain in the world?  
> &gt; quiz.showMe\(\)  
> Everest  
> &gt; quiz.next\(\)  
> Ok  
> &gt; quiz.quizMe\(\)  
> What is the highest mountain in Scotland?

Có thể viết bằng cách tạo 1 namespace  bằng obj quiz   


```javascript
var quiz = {
    questions: [{
            question: "What is the highest mountain in the world?",
            answer: "Everest"
        },
        {
            question: "What is the highest mountain in Scotland?",
            answer: "Ben Nevis"
        },
        {
            question: "How many munros are in Scotland?",
            answer: "284"
        }
    ],
    index: 0,

    showme: function () {
        console.log(this.questions[this.index].answer);
    },
    quizeMe: function () {
        console.log(this.questions[this.index].question);
    },
    next: function () {
        this.index++
            console.log('next question');
    }
}
```

Vấn đề  của cách viết này là người ta có thể access vào biến anserwer

> quiz.question\[2\].answer  
> 284

Với các ngôn ngữ khác thì class sẽ các biến private cũng như public thì  như js sẽ làm thế nào ?  
==&gt; dùng function expression

Các các biến trong hàm chỉ có thể truy cập được với các hàm ở bên trong\(inner function\), nhưng cái này cũng bình thường với các ngôn ngữ khác. Điều thú vị ở JS chính là closure.

Nhờ closure mà giá trị của biến index khi hàm quiz.next\(\) được tăng lên và  giữ nguyên ở giá trị 1,  
Do đó những lần gọi sau mà quiz.quizeMe\(\) và quiz.showme\(\) sẽ gọi với index bằng 1.  
\(Mở rộng là đối với các ngôn ngữ khác, biến local trong hàm đó sẽ bị mất đi khi  hàm đó được thực hiện xong\)

```javascript
var quiz = (function () {
    var questions = [{
            question: "What is the highest mountain in the world?",
            answer: "Everest"
        },
        {
            question: "What is the highest mountain in Scotland?",
            answer: "Ben Nevis"
        },
        {
            question: "How many munros are in Scotland?",
            answer: "284"
        }
    ]
    var index = 0

    return {
        showme: function () {
            console.log(questions[index].answer);
        },
        quizeMe: function () {
            console.log(questions[index].question);
        },
        next: function () {
            index++
            console.log('next question');
        }
    }
})() // IIFE (Immediately Invoked Function Expression) 

quiz.next()     => index = 1
quiz.quizeMe()  => question: "What is the highest mountain in Scotland?",
quiz.showme()   => answer: "Ben Nevis"
```



Một điều thú vị nữa là nhờ IIFE \(_Immediately Invoked Function_ Expression\)  mà có thể viết một cách rất đẹp =&gt; quiz.next\(\), còn không có thì phải viết là  quiz\(\).next\(\)  


## Public vs Private

Thế trường hợp muốn dùng cả public, private thì sao ?

```javascript
var Person = function (name, age) {
    this.name = name;
    var age = age;
    this.getAge = function () {
        return age
    }
}

var real_person = new Person('nhạt', 69)
console.log(real_person.name);
console.log(age);                // undefined
var age = real_person.getAge() 
console.log(age);                // 69
```



## Dùng Class trong ES6

Với class thì private var và các hàm thao tác với biến chỉ có thể đặt trong hàm tạo\(constructor\) 

```javascript
class Person {
    constructor(name) {
        this.name = name; // this is public
        var _age = 20; // this is intended to be private
        this.greet = function () {
            console.log(`name: ${this.name}, age: ${_age}`);
        }
    }

    hello() {
        console.log(`Hi, my name is ${this.name}`);
    }
}

let joe = new Person('Joe');
joe.greet();
joe.hello()
```

