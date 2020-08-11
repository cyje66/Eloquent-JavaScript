## Methods
用push()、pop()可以新增或刪除`array`中的資料
```
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push(5);
console.log(sequence);
// → [1, 2, 3, 4, 5]
console.log(sequence.pop());
// → 5
console.log(sequence);
// → [1, 2, 3, 4]
```
## Types
JavaScript 的資料型態有七種- *字串（string）、數字（number）、布林值（boolean）、null、undefined、物件（object）與 symbol。*
其中函式（function）和陣列（array）、日期（date）皆為物件的一種，function 是可呼叫的物件，而 array 是結構較嚴謹的物件。
### typeof
```
typeof 'Hello World!'; // 'string'
typeof true; // 'boolean'
typeof 1234567; // 'number'
typeof null; // 'object'
typeof undefined; // 'undefined'
typeof { name: 'Jack' }; // 'object'
typeof Symbol(); // 'symbol'
typeof function() {}; // 'function'
typeof [1, 2, 3]; // 'object'
typeof NaN; // 'number'
```
這裡會看到幾個有趣的（奇怪的）地方…

* null 是基本型別之一，但 typeof null 卻得到 object，而非 null！這可說是一個 bug，可是若因為修正了這個 bug 則可能會導致很多網站壞掉，因此就不修了！
* 雖然說 function 是物件的子型別，但 typeof function() {} 是得到 function 而非 object，和陣列依舊得到 object 是不一樣的。
* NaN 表示是無效的數字，但依舊還是數字，因此在資料型別的檢測 typeof NaN 結果就是 number，不要被字面上的意思「不是數字」（not a number）給弄糊塗了。
另外，NaN 與任何數字運算都會得到 NaN，並且 NaN 不大於、不小於也不等於任何數字，包含 NaN 它自己。  
...  
另外，如果想知道這個物件到底是屬於哪個子型別，則可使用 Object.prototype.toString 來檢視 [[Class]] 這個內部屬性。
```
Object.prototype.toString.call([1, 2, 3]); // "[object Array]"
Object.prototype.toString.call({ name: 'Jack' }); // "[object Object]"
Object.prototype.toString.call(function sayHi() {}); // "[object Function]"
Object.prototype.toString.call(/helloworld/i); // "[object RegExp]"
Object.prototype.toString.call(new Date()); // "[object Date]"
```
[參考這個網站](https://cythilya.github.io/2018/10/24/object/)
## Objects
宣告方式如下:
```
let descriptions = {
  work: "Went to work",
  "touched tree": "Touched a tree"
};
```
其中，`work`可以用`descriptions.work`來存取他，但`touched tree`就要用`descriptions[touched tree]`來存取，其實第二種是為了要讓一些以特殊符號取名的key所設計的，例如:
```
const obj = {
  '!!12345!!': 'Hello World',
};

obj.!!12345!! // Uncaught SyntaxError: Unexpected token !
obj['!!12345!!'] // "Hello World"
```
### 內容(Contents)
物件的內容是由屬性組成的，而屬性是由 key-value pair 構成，value 可為任意資料型別的值，並且值是以參考（reference）的方式（存位置）儲存。  

如何存取物件的屬性呢？有兩種方式

* 特性存取（property access），意即 `.`
* 鍵值存取（key access），意即 `[ ]`  
  
`Object.keys` 回傳一Object的屬性(property): 
```
console.log(Object.keys({x: 0, y: 0, z: 2}));
// → ["x", "y", "z"]
```
`Object.assign`把一object裡的屬性複製到另一object中:
```
let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
console.log(objectA);
// → {a: 1, b: 3, c: 4}
```
