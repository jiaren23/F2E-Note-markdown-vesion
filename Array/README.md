# Array 常見陣列操作
DEOM Code：[for & forEach & map](https://codepen.io/jiaren/pen/vYLWqrK?editors=0012)<br>
DEOM Code：[filter](https://codepen.io/jiaren/pen/NWxXWey?editors=0011)<br>
DEOM Code：[sort](https://codepen.io/jiaren/pen/GRoygqO?editors=0011)<br>
DEOM Code：[reduce](https://codepen.io/jiaren/pen/JjGMoJR?editors=0010)<br>

進階 : <br>
DEOM Code：[Javascript 30 Day 4 ](https://github.com/jiaren23/Javascript-30-days/tree/master/js30-04_Array%20Cardio%20Day%201)
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
<hr>

## **filter**
* 不會改變原始陣列
* 返回陣列，包含了符合條件的所有元素。如果沒有符合條件的元素則返回空陣列
* 有回傳值 

範例 : 
基本使用 : 
```js
    let arrOne = [1, 2, 3, 4, 5, 6, 9, 10, 15];
    let newArrOne = arrOne.filter( item => {
    　　return item % 2 !== 0;
    });
    console.log(newArrOne) // [1, 3, 5, 9, 15]
```
```js
    let arr = ['A', '', 'B', null, undefined, 'C', ' '];
    let arrFilter = arr.filter(item => {
    　　return item && item.trim(); // trim() 方法用以刪除空白字符
    });
    console.log(arrFilter)         // ["A", "B", "C"]
```

搭配物件 : 有一群人 , 要篩選出 1500 年代出生的人的資料 : 
```js
    const persons = [
        { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
        { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
        { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
        { first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
        { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
    ];

    let generation15 = persons.filter( item =>{
        return item.year >= 1500 && item.year < 1600 
    })

    console.log(generation15) //  [{ first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },{ first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 }]
```

搭配物件 : 有一群人 , 要篩選出 1500 年代出生的人 : ( 針對以上資料再做一層迴圈渲染出 `first` )
```js
    const persons = [
        { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
        { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
        { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
        { first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
        { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
    ];

    let generation15 = persons.filter( item =>{
         return item.year >= 1500 && item.year < 1600 
    }).map( item =>{           // 這裡用 map 原因是為了回傳 值出去給 generation15 
         return item.first
    })

    console.log(generation15) // ["Galileo", "Johannes"]
```
<hr>

## **sort**
* 排序陣列
* 一般對陣列直接進行 .sort() 方法時會使陣列內數字、字串做 `升冪排列`  , 但 MDN 表示 sort 排序不一定是穩定的（stable）
* 所以大部分我們在用 sort 會加入 `a` & `b` 兩參數 , 使結果 `return a-b  或是 b-a ` 來達到 `升冪` 或 `降冪排列` 。 
* 內部運作原理 : <br>
    如果 `a-b < 0` 那就 `a 擺前面` <br>
    如果 `a-b == 0 ` 那就 `a 與 b 順序不變 `<br>
    如果 `b-a > 0 ` 那就 ` b 擺前面 `

範例 : 
基本使用 : 
```js
    const person = [
      { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
      { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
      { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
    ];

    const ansSort = person.sort((a, b)=>{
      return a.year - b.year;             // -(b.year-a.year)
    });

    console.table(ansSort);              // 依照出生年代進行升覓排序
```
另一種寫法 : 此寫法原理 : 只要不是 ` a > b ` 的 都會讓 ` b 在前面`
```js
   const ansSort = person.sort((a, b)=>{
      return a.year > b.year ? 1 : -1 ;  
    });
```

<hr>

## **reduce**
* 累加陣列
* reduce() 要給定兩個參數 , ` reduce( function , 累加的初始值) `
* 針對上方 , 第一個參數的 function 又要給定兩個參數 ` function( 對應累加的初始值參數 , item ) `

範例 : 
基本使用 : 
```js
    const array1 = [1, 2, 3, 4];

    let red  = array1.reduce( (init,item) =>{
         return init += item
    }, 0 )

    console.log(red);  // 1 + 2 + 3 + 4 = 10
```
基本使用 : callback function :
```js
    const array1 = [1, 2, 3, 4];
    
    let reducer = (init , item)=>{
            return init += item
    }

    console.log( array1.reduce(reducer, 5) ); // 5 + 1 + 2 + 3 + 4
```

搭配物件 : 有一群人 , 他們的壽命加總共是 多少年<br>
`forEach 寫法 : ( 早期還沒有 reduce() 時的作法)`
```js
    const person = [
      { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
      { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
      { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
    ];

    let agesTotal = 0;
    person.forEach(item=>{
      agesTotal += (item.passed - item.year)
    })

    console.log(agesTotal) // 219
```
`reduce 寫法 :`
```js
    const person = [
      { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
      { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
      { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
    ];

      const Total = person.reduce((total,item)=>{  
      return total+ (item.passed - item.year)
    },0)

    console.log(Total) //219
```



