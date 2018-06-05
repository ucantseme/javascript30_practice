## Array Cardio Day 1

### 內容

#### Array.prototype.filter()
用`true`、`false`判斷，回傳一組新陣列。

#### Array.prototype.map()
回傳新陣列並修改內容，不回傳會變`undefined`。

#### Array.prototype.sort()
用`大於0`、`等於0`、`小於0`判斷。

範例中使用判斷式來排列
```javascript
inventors.sort( (a, b) => a.year>b.year?'1':'-1' )
```

也可改成用計算的方式
```javascript
inventors.sort( (a, b) => a.year - b.year )
```
#### Array.prototype.reduce()
參數
* 初始值
* 目前處理中的值
* 目前處理中的索引值
* 呼叫reduce的陣列

#### split()
`str.split(要分割的對象, 數量)`，傳回陣列。

#### 第八題
範例使用reduce
```javascript
const transportation = data.reduce(function (obj, item) {
      if(!obj[item]) obj[item] = 0
      obj[item]++
      return obj
    },{})
    console.log(transportation)
```
可以改成用forEach
```javascript
const obj = {}
    data.forEach(function (item) {
      if(!obj[item]) obj[item] = 0
      obj[item]++
    })
    console.log(obj)
```