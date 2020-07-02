# Array 常見陣列操作
<hr>

## **forEach**
* `forEach` 跟 `for` 迴圈差不多用法 
* 可以遍歷陣列

範例 :
產生一新陣列 , 並對新內容進行 乘 2 動作 <br>

`for 寫法 :`
```js
    let ary = [ 1 , 2 , 3 , 4 , 5 ];
    let emptyOne = [];
    for(let i=0;i<ary.length;i++){
        emptyOne.push( ary[i] * 2 )
    }
    console.log(emptyOne) // [2, 4, 6, 8, 10]
```
`forEach 寫法 :`
```js
    let ary = [ 1 , 2 , 3 , 4 , 5 ];
    let emptyTwo = [];
    ary.forEach( ( item, index ) => {
        emptyTwo.push(item * 2) ; 
    });
    console.log(emptyTwo) // [2, 4, 6, 8, 10]
```
這裡先提一下 `map 寫法 :` ( 不須事先準備好空陣列來存新陣列 , 而是透過 `return 值` 賦予到新變數 )
```js
    let ary = [ 1 , 2 , 3 , 4 , 5 ];
    let newMapArray = ary.map( ( item, index ) => {
        return item * 2 ; 
    });
    console.log(newMapArray) // [2, 4, 6, 8, 10]
```
* `forEach` 與 `map` 寫法也相似
* 但沒有回傳值 
* 當使用 陣列索引會 ` 改變原始陣列  `!!!

範例 :
證明 `forEach` 沒有回傳值 , 且當使用 `陣列索引`會改變原始陣列 <br>

```js
    let aryTwo = [ 1 , 2 , 3 , 4 , 5 ];
    let newAry = aryTwo.forEach((item, index , ary)=>{
        ary[index] = item * 2
    })
    console.log(newAry); // undefined => 本身沒有 return 效果 (寫return 也沒用)
    console.log(aryTwo); // [2, 4, 6, 8, 10]  => 原始陣列遭改變了
```
<hr>

## **map**
* 可以遍歷陣列
*  `map` 與 `forEach` 寫法也相似
* 有回傳值 

範例 : 
展示一下 `map` 與 `forEach` 的使用和差異 : 
```js
let testAry = [1,2,3,4,5,6];

let newMap = testAry.map(item=>{
  return item * 2
})
console.log(testAry) // [1, 2, 3, 4, 5, 6] => 原始陣列不變
console.log(newMap)  // [2, 4, 6, 8, 10, 12]

let newForEach = testAry.forEach(item=>{
   item * 2
})
console.log(testAry)    // [1, 2, 3, 4, 5, 6] => 原始陣列不變
console.log(newForEach) // undefined => 本身沒有 return 效果 (寫return 也沒用)
```

* 當使用 陣列索引也會 ` 改變原始陣列  `, 但可以產生新陣列 , 且能賦予在其他變數

範例 :
證明 `map` 有回傳值 , 且當使用 `陣列索引`會改變原始陣列 <br>

```js
    let aryThree = [ 1 , 2 , 3 , 4 , 5 ];
    let newAryMap = aryThree.map((item, index, ary)=>{
         return ary[index] = item * 2 ;
    })
    console.log(newAryMap) // [2, 4, 6, 8, 10] => return 將有效果 成功賦予到 newAryMap
    console.log(aryThree)  // [2, 4, 6, 8, 10] => 原始陣列遭改變了
```


