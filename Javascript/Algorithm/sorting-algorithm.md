#### <em>算法是指解题方案的准确而完整的描述,是一系列解决问题的清晰指令,算法代表着用系统的方法描述解决问题的策略机制。一个算法的优劣可以用空间复杂度和时间复杂度来衡量。</em>
![Alt text](./imgs/png.png);

# JS 10大经典算法

## 1.冒泡排序 
### 平均时间复杂度O(n^2)  空间复杂度O(1) 稳定
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

## 2.选择排序
### 平均时间复杂度O(n^2)  空间复杂度O(1) 不稳定
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

## 3.快速排序
### 平均时间复杂度O(nlogn)  空间复杂度O(logn) 不稳定
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

# 4.插入排序
### 平均时间复杂度O(n^2)  空间复杂度O(1) 稳定
```
function insertSort(arr) {
  let len = arr.length;
  let preIndex, current;
  for(let i = 1; i < len; i++) {
    preIndex = i - 1;
    current = arr[i];
    while(preIndex >= 0 && current < arr[preIndex]) {
      arr[preIndex + 1] = arr[preIndex];
      preIndex--;
    }
    arr[preIndex + 1] = current; 
  }
  return arr;
}
```

# 5.希尔排序
### 平均时间复杂度O(nlogn)  空间复杂度O(1) 不稳定
```
function shellSort(arr) {
  let len = arr.length;
  for(let gap = Math.floor(len / 2); gap > 0 ; gap = Math.floor(gap / 2)) {
    for (let i = gap; i < len; i++) {
      let j = i;
      let current = arr[i];
      while(i - gap >= 0 && current < arr[j - gap]) {
        arr[j] = arr[j - gap];
        j = j - gap
      }
      arr[j] = current;
    }
  }
  return arr;
}
```

## 6.归并排序
### 平均时间复杂度O(nlogn)  空间复杂度O(n) 稳定
```
function mergeSort(arr) {
  let len = arr.length;
  if(len < 2) {
    return arr;
  }
  let middle = Math.floor(len / 2),
    left = arr.slice(0, middle),
    right = arr.slice(middle);
  return merge(mergeSort(left), mergeSort(right));
}
function merge(left, right) {
  let result = [];
  while (left.length > 0 && right.length > 0) {
    if(left[0] <= right[0]) {
      result.push(left.shift());
    }else {
      result.push(right.shift())
    }
  }
  while (left.length) {
    result.push(left.shift())
  }
  while (right.length) {
    result.push(right.shift())
  }
  return result
}
```

## 7.堆排序
### 平均时间复杂度O(nlogn)  空间复杂度O(1) 不稳定
```
var len;   // 因为声明的多个函数都需要数据长度，所以把len设置成为全局变量
 
function buildMaxHeap(arr) {  // 建立大顶堆
  len = arr.length;
  for(var i = Math.floor(len/2); i >= 0; i--) {
      heapify(arr, i);
  }
}
 
function heapify(arr, i) {    // 堆调整
  var left = 2 * i + 1,
    right = 2 * i + 2,
    largest = i;

  if(left < len && arr[left] > arr[largest]) {
    largest = left;
  }

  if(right < len && arr[right] > arr[largest]) {
    largest = right;
  }

  if(largest != i) {
    swap(arr, i, largest);
    heapify(arr, largest);
  }
}
 
function swap(arr, i, j) {
  var temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
 
function heapSort(arr) {
  buildMaxHeap(arr);

  for(var i = arr.length - 1; i > 0; i--) {
    swap(arr, 0, i);
    len--;
    heapify(arr, 0);
  }
  return arr;
}
```

## 8.计数排序
### 平均时间复杂度O(n * k)  空间复杂度O(k) 稳定
```
function countingSort(arr, maxValue) {
  let bucket = new Array(maxValue+1),
      sortedIndex = 0;
      arrLen = arr.length,
      bucketLen = maxValue + 1;

  for (let i = 0; i < arrLen; i++) {
      if (!bucket[arr[i]]) {
          bucket[arr[i]] = 0;
      }
      bucket[arr[i]]++;
  }

  for (let j = 0; j < bucketLen; j++) {
      while(bucket[j] > 0) {
          arr[sortedIndex++] = j;
          bucket[j]--;
      }
  }

  return arr;
}
```

## 9.桶排序
### 平均时间复杂度O(n + k)  空间复杂度O(n + k) 稳定
```
function bucketSort(arr, bucketSize) {
  if (arr.length === 0) {
    return arr;
  }

  let i;
  let minValue = arr[0];
  let maxValue = arr[0];
  for (i = 1; i < arr.length; i++) {
    if (arr[i] < minValue) {
      minValue = arr[i];                
    } else if (arr[i] > maxValue) {
      maxValue = arr[i];               
    }
  }

  //桶的初始化
  let DEFAULT_BUCKET_SIZE = 5;          
  bucketSize = bucketSize || DEFAULT_BUCKET_SIZE;
  let bucketCount = Math.floor((maxValue - minValue) / bucketSize) + 1;   
  let buckets = new Array(bucketCount);
  for (i = 0; i < buckets.length; i++) {
    buckets[i] = [];
  }

  //利用映射函数将数据分配到各个桶中
  for (i = 0; i < arr.length; i++) {
    buckets[Math.floor((arr[i] - minValue) / bucketSize)].push(arr[i]);
  }

  arr.length = 0;
  for (i = 0; i < buckets.length; i++) {
    insertSort(buckets[i]);                    
    for (var j = 0; j < buckets[i].length; j++) {
      arr.push(buckets[i][j]);                      
    }
  }

  return arr;
}
```
## 10.基数排序
### 平均时间复杂度O(n * k)  空间复杂度O(n + k) 稳定
```
var counter = []; 
function radixSort(arr, maxDigit) {
  let mod = 10;
  let dev = 1;
  for (let i = 0; i < maxDigit; i++, dev *= 10, mod *= 10) {
    for(let j = 0; j < arr.length; j++) {
      let bucket = parseInt((arr[j] % mod) / dev);
      if(counter[bucket]==null) {
          counter[bucket] = [];
      }
      counter[bucket].push(arr[j]);
    }
    let pos = 0;
    for(let j = 0; j < counter.length; j++) {
      let value = null;
      if(counter[j]!=null) {
        while ((value = counter[j].shift()) != null) {
          arr[pos++] = value;
        }
      }
    }
  }
  return arr;
}
```