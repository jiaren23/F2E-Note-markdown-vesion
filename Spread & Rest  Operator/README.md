# Speead & Rest Operator 常見展開、其餘運算 操作


## **Spread Operator 展開運算符**
* 使用 `...變數名稱` 撰寫
* 有複製 陣列的特性 , 解決陣列物件傳址 ( 傳參考 ) 的特性
* 有複製 陣列的特性 , 解決 ` querySelectorAll 選出來是 Nodelist 類陣列 ` 的特性

範例 :
合併兩陣列 <br>

`ES5 寫法 :`
```js
    let ary = ['a','b','c'];
    let ary2 = ['d','e','g'];

    console.log( ary.concat(ary2) ) // ["a", "b", "c", "d", "e", "g"]
```
`ES6 寫法 :`
```js
    let ary = ['a','b','c'];
    let ary2 = ['d','e','g'];
        
    console.log( [...ary,...ary2] ); // ["a", "b", "c", "d", "e", "g"]
```

範例 :
使用展開運算符解決 陣列傳址 (傳參考) 的情況 <br>

`原始陣列傳址特性 ary 將也會跟著被改變 :`
```js
    let ary = ['a','b','c'];
    let newAry = ary;
    newAry.push('ming') // push 小名進去新陣列
        
    console.log(ary);   // ["a", "b", "c", "ming"]
```
`Spread 寫法 , ary 保持不變 :`
```js
    let ary = ['a','b','c'];
    let newAry = [...ary] ; // 相同於複製一份起來的概念
    newAry.push('ming')

    console.log(ary)        // ["a", "b", "c"]
```

範例 :
使用展開運算符解決 querySelectorAll 篩選 DOM 會生成  ` Nodelist 類陣列  `的特性 <br>

`Spread 寫法 改變 類陣列情形 :`
```js
    let dom = document.querySelectorAll('li');

    console.log( dom );       // NodeList(5) [li, li, li, li, li]
    console.log( [...dom] );  // [li, li, li, li, li]
```

範例 :
使用展開運算符解決 function 內  ` arguments ` 結果會是 ` 類陣列  `的特性 <br>

` Spread 寫法 改變 類陣列情形 : `
```js
    function ary(){
        console.log( arguments )    // Arguments array 類陣列
        console.log( ...arguments ) // [1, 2, 3, 4, 5, 6]
    }
    let num = [1,2,3,4,5,6];
    ary(num) ; 
```

` 因轉成純陣列  所以可以使用 reduce() : `
```js
    function ary() {
        let arg = [...arguments];
        let total = arg.reduce((init, current) => {
            return init + current
        })
        console.log(total)  // 1 + 2 + ... = 21

    }
    ary(1, 2, 3, 4, 5, 6)
```

<hr>

## **Rest Operator 其餘參數**

* 在不清楚參數數量的時候 透過 ` ...參數 ` 來撰寫

```js
    function Rest(...all){

         console.log(all)   // [1, 2, 34, 5, 6]

    }
    Rest(1 ,2 ,34 , 5, 6)
 ```

 ` 如果有特別要指定的參數時 一樣可以另外註明 做使用`

```js
    function Rest(name, ...all){
        
        console.log(name)  // ming
        console.log(all)   // ["a", "a", "d", "w", "w", "e"]

    }
    Rest('ming','a','a','d','w','w','e')

 ```
