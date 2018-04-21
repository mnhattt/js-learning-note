

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



