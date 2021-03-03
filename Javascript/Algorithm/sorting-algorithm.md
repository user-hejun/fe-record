# JS 10大经典算法

## 冒泡排序 
### 时间复杂度O(n^2)  空间复杂度O(1) 稳定
```
function bubbleSort(arr) {
  let len = arr.length;
  for(let i = 0; i < len; i++) {
    for(let j =0; j < len - 1 - i; j++) {
      if(arr[j] > arr[j+1]) {
        temp = arr[j+1]
        arr[j+1] = arr[j]
        arr[j] = temp;
      }
    }
  }
  return arr;
}
```

## 选择排序
### 时间复杂度O(n^2)  空间复杂度O(1) 稳定
```
function selectionSort(arr) {
  let len = arr.length;
  let minIndex, temp;
  for(let i = 0; i < len - 1 ; i++) {
    minIndex = i;
    for(let j = i + 1; j < len; j++) {
      if(arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }
    temp = arr[i];
    arr[i] = arr[minIndex];
    arr[minIndex] = temp;
  }
  return arr;
}
```

# 快速排序
### 时间复杂度O(n^2)  空间复杂度O(1) 不稳定
```
function quickSort(arr) {
  let len = arr.length;
  let midIndex = Math.floor(len / 2);
  let left = []
  let right = [];
  if(len <= 1) {
    return arr;
  }
  let midValue = arr.splice(midIndex, 1)[0];
  for(let i = 0; i < len-1; i++) {
    if(arr[i] >= midValue) {
      right.push(arr[i])
    }else {
      left.push(arr[i])
    }
  }
  return quickSort(left).concat(midValue, quickSort(right));
}
```

