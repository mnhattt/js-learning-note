## work and not work

```
var Button = (function () {
    this.count = 0
    this.click = function () {
        this.count++
            console.log(this.count);
    }
})

var button = new Button()

setTimeout(button.click, 500);

// work
var Button = (function () {
    this.count = 0
    this.click = () => {
        this.count++
            console.log(this.count);
    }
})

var button = new Button()

setTimeout(button.click, 500);
```

trong arrow function, this sẽ luôn bind với obj mà nó được tạo ra, mà ở đây this sẽ luôn bound với button ở BẤT CỨ chổ nào nào đợc gọi.

trong class Button ta dùng arr để bind this.count, nên lúc tạo ra button this.count trong this.click sẽ luôn bound với button

