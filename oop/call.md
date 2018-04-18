```
function product(num, factor) {
    return num * factor
}

function double (num) {
    return product(num, 2)
}

console.log(double(4));
```

### dùng 1 lần call 

```
function product(num, factor) {
    return num * factor
}

function double(num) {
    return product(this, 2)
}

console.log(double.call(4));
```

### dùng 2 lần call

```
function product(factor) {
    return this * factor
}

function double (num) {
    return product.call(this, 2)
}

console.log(double.call(4));
```



