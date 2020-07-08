# Destructuring Assignment 解構賦值 常見 操作

## **陣列 解構賦值**
* 類似鏡射的感覺 , 將等號右邊的陣列 解析到左邊對應的位置 
* 其餘沒有寫出來的對應位置 一樣使用 `...變數名稱` 撰寫 取代剩餘的陣列內容

範例 :
基本陣列解構<br>

`陣列解構 :`
```js
    let family = ['ming','jia','circle','yaa']
    let [ dad, mom, ...other] = family;
    console.log( dad )   //  ming  型別 : 陣列
    console.log( other ) // ["circle", "yaa"]
```

範例 :
交換 兩個人的值<br>

` 傳統要在新增一值 來暫存內容 寫法 :`
```js
    let aaa = 'jie';
    let bbb = 'lebron';
    let ccc = '';
    ccc = aaa;
    aaa = bbb;
    bbb = ccc ;
    
    console.log( aaa , bbb );   // lebron jie
```

` 陣列解構 寫法 :`
```js
    let aaa = 'jie';
    let bbb = 'lebron';

    [bbb,aaa] = [aaa,bbb];
    console.log( aaa , bbb );   // lebron jie
```


範例 :
拆解字元 <br>

`陣列解構 :`
```js
    let str = "HAPPY8";
    let [a,b,c,d,e,f] = str
    console.log(a,b,c,d,e,f) // H A P P Y 8
```
<hr>

## **物件 解構賦值**
* 解構名稱要 與 欲解構 key 值一樣名稱
* 物件解構常用於監聽的  ` e.target ` 裡面有 name value 等等值 做使用


範例 :
基本物件解構<br>

`物件解構 :`
```js
    let items = {
        name:23 ,
        value:56
    }

    let {name,value} = items;

    console.log(name)  // 23
```

範例 :
進階 物件解構 : 將解構 key 值改成一個新 名稱<br>

`物件解構 :`
```js
    let Family = {
         Gin:   '勤',
        July: '竭力',
        bot : '伯特'
    }

    let {Gin} = Family;
    console.log(Gin)            // 勤

    let {Gin:newGin} = Family;  // 這裡重新賦予 Gin 一個新的 key 名稱
    console.log(newGin)         // 勤
```