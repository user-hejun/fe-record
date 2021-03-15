# 数组去重

## 双重for循环
```
function unique1(arr) {
    let len = arr.length;
    for(let i = 0; i < len; i++) {
        for(let j = i + 1; j < len; j++) {
            if(arr[j] === arr[i]) {
                arr.splice(j, 1);
                j--;
            }
        }
    }
    return arr;
}
```

## hash-key 去重
```
function unique2(arr) {
    let len = arr.length,
        result = [],
        hash = {}
    for(let i = 0; i < len; i++) {
        let key = arr[i] + typeof(arr[i]);
        if(!hash[key]) {
            result.push(arr[i]);
            hash[key] = true;
        }
    }
    return result;
}
```

## ES6 Set去重
```
function unique3(arr) {
    return Array.form(new Set(arr))
}
```

```
function unique4(arr) {
    return [...new Set(arr)]
}
```

