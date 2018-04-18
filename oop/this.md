Khi một hàm được thực thi\\(hay được gọi\\) thì luôn có một ngữ cảnh\\(excution context\\) để hàm đó thực thi.  Ngữ cảnh đó chính là \*\*this\*\*. Muốn xác định this thì luôn phải đặt câu hỏi, ngữ cảnh mà hàm đó đang thực thi là gì



\#\#\#\#\# Khi hàm được gọi thẳng mà không thông qua bất cứ obj nào thì bối cảnh của nó sẽ là global hoặc undifine\\(nếu dùng 'use strict';\\)



\`\`\`

// 'use strict';



var Func = function \(\) {

    console.log\(this\);

}



Func\(\)

new Func\(\)

\`\`\`



Khi một hàm được gọi bởi 1 obj thì obj đó được ngầm pass vào vào hàm



\`\`\`

var Func = function \(\) {

    this.abc = 'xyz'

    this.log = function \(\) {

        console.log\(this\);

    }

}

var func = new Func\(\)

func.log\(\) 

// this = func 

// console.log\(this\) = Func { abc: 'xyz', log: \[Function\] }



var func = {

    abc: 'xyz',

    log: function \(\) {

        console.log\(this\)

    }

}



func.log\(\) 

// this = func 

// console.log\(this\) =  { abc: 'xyz', log: \[Function\] }

\`\`\`



Thử nghiệm một tí



\`\`\`

var Func = function \(\) {

    this.abc = 'xyz'

    this.log = function \(cb\) {

        cb\(\)

    }

}



new Func\(\).log\(function \(\) {

    console.log\(this\);

}\)





var func = {

    abc: 'xyz',

    log: function \(cb\) {

        cb\(\)

    },

}



func.log\(function \(\) {

    console.log\(this\);

}\)

// this = ???

\`\`\`



\#\# chủ động thay đổi ngữ cảnh với bind, call, apply



thí nghiệm ở trên làm cho ngữ cảnh thay đổi từ obj sang global, giờ ta sẽ đưa nó về lại obj bằng bind



\`\`\`

var func = {

    abc: 'xyz',

    log: function \(cb\) {

        cb\(\)

    },

}



func.log\(\(function \(\) {

    console.log\(this\);

}\).bind\(func\)\)

// nhờ bind thì this = func 

// console.log\(this\) = console.log\(func\)





var func = {

    abc: 'xyz',

    log: function \(cb\) {

        cb.apply\(this\) \(1\)

    },

}



func.log\(function \(\) {

    console.log\(this\); \(2\)

}\)

// dùng call/apply thì phải đưa lên trên hàm callback

// this được đưa vào apply\(1\) chính là this lúc gọi hàm log, là đối tượng func

// do đó lúc log ra this\(2\) chính là log ra đối tượng func

\`\`\`

