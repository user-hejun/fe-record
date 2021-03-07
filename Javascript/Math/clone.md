# 浅拷贝与深拷贝
## 浅拷贝实现
```
1. 直接用 = 赋值
2. Object.assign()
3. for...in只循环第一层
```

## 深拷贝实现
### 乞丐版深拷贝
```
JSON.parse(JSON.stringify())
```

### 基础版本深拷贝
```
function clone(obj) {
    let cloneObj = {}
    for(let key in obj) {
        if(typeof obj[key] === 'object') {
            cloneObj[key] = clone(obj[key])
        } else {
            cloneObj[key] = obj[key]
        }
    }
    return cloneObj;
}
```


### 改进版深拷贝
```
const isComplexDataType = obj => (typeof obj === 'object' || typeof obj === 'function') && (obj !== null);
const deepClone = function(obj, hash = new WeakMap()) {
    if(obj.constructor === Date) {
        return new Date(obj)
    }
    if(obj.constructor === RegExp) {
        return new RegExp(obj)
    }
    if(hash.has(obj)) {
        return hash.get(obj)
    }
    let allDesc = Object.getOwnPropertyDescriptors(obj)
    let cloneObj = Object.create(Object.getPrototypeOf(obj))
    hash.set(obj, cloneObj)
    for(let key of Reflect.ownKeys(obj)){
        cloneObj[key] = (isComplexDataType(obj[key]) && typeof obj[key] !== 'function') ? deepClone(obj[key], hash) : obj[key]
    }
    return cloneObj;
}
```
* 验证代码
```
let obj = {
    num: 0,
    str: '',
    boolean: true,
    unf: undefined,
    nul: null,
    obj: { name: '对象', id: 1},
    [Symbol('1')]: 1,
    date: new Date(),
    reg: new RegExp('/我是正则/ig'),
    arr: [0,1,2],
    func: function() {console.log('我是一个函数')},
};

Object.defineProperty(obj, 'innumerable', {
    enumerable: false, value: '不可枚举属性'
})
obj = Object.create(obj, Object.getOwnPropertyDescriptors(obj)) 
obj.loop = obj;
let cloneObj = deepClone(obj);
cloneObj.arr.push(4);
console.log('obj', obj);
console.log('cloneObj', cloneObj);
```