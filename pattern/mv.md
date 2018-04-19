Nếu dữ liệu\(obj/model\) làm việc trực tiếp với view thì việc thay đổi view hay model sẽ rất phức tạp, thay đổi cái này sẽ phải thay đổi cái kia. Cần có 1 khâu trung gian để việc thay đổi chỉ diễn ra ở khâu này. 

Nên dù gọi thế nào thì ta chỉ có 2 thành phần không thay đổi là Model và View.

## Áp dụng module  pattern để xây dựng cấu trúc MV\*

### Note app

```
//model
var Data = (function () {
    var init = function () {
        if (!localStorage.notes)
            localStorage.notes = JSON.stringify([])
    }

    var addNote = function (note) {
        var data = JSON.parse(localStorage.notes)
        data.push(note)
        localStorage.notes = JSON.stringify(data)

    }

    var getAllNote = function () {
        return JSON.parse(localStorage.notes)
    }

    return {
        init: init,
        addNote: addNote,
        getAllNote: getAllNote
    }
})()

var View = (function () {
    var render = function (notes) {
        notes.forEach(note => {
            console.log(note + '\n');
        });
    }
    return {
        render: render
    }
})()

var App = (function () {
    var init = function () {
        Data.init()
        View.render(Data.getAllNote())
    }

    var addNote = function (note) {
        Data.addNote(note)
        View.render(Data.getAllNote())
    }

    return {
        init: init,
        addNote: addNote,
    }
})()

App.addNote('123')
> 
```



