## Functions
### 宣告方式
* Functions as values
宣告一個變數，並把他指定給某個function，宣告完後要加上";"，例如:
```
const square = function(x) {
  return x * x;
};

console.log(square(12));
// → 144
```
* Declaration notation
一般的宣告，宣告完後不用加";"
```
function square(x) {
  return x * x;
}
```
* Arrow functions
跟第一種不同的地方是，他用`=>`的符號取代`function`，It expresses something like “this input (the parameters) produces this result (the body)”.其實他跟第一種宣告的方式並沒有明顯的差異
，主要是為了讓function的宣告看起來不那麼的冗長。
```
const power = (base, exponent) => {
  let result = 1;
  for (let count = 0; count < exponent; count++) {
    result *= base;
  }
  return result;
};
```
如果沒有傳遞參數的話，括號裡面就不放東西:
```
const horn = () => {
  console.log("Toot");
};
```
## Optional Arguments
在javascript中，呼叫function時，多加參數時他會自動忽略掉，少加參數時他會把`undefined`指定給不見的參數，並不會影響到他的執行，例如:
```
function square(x) { return x * x; }
console.log(square(4, true, "hedgehog"));
// → 16
```
讓我們看看活用這個機制的例子:
```
function minus(a, b) {
  if (b === undefined) return -a;
  else return a - b;
}

console.log(minus(10));
// → -10
console.log(minus(10, 5));
// → 5
```
## Closure
讓某個特定的`instance`在一個封閉的範圍內可以參照一個`local binding`，稱之。例如:
```
function wrapValue(n) {
  let local = n;
  return () => local;
}

let wrap1 = wrapValue(1);
let wrap2 = wrapValue(2);
console.log(wrap1());
// → 1
console.log(wrap2());
// → 2
```
當function被呼叫時，他會去找他被"創造"出來的環境，而不是被"呼叫"的環境，例如:
```
function multiplier(factor) {
  return number => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));
// 10
```
在這個例子中，`multiplier`被呼叫且創造了一個`factor`被指定為2的環境，而這個function return值被儲存在`twice`，`twice`記住了這個環境。所以當他被呼叫時，他會把傳進來的參數乘以2。

## Excercise
```
// Your code here.
function countBs(s){
  let count = 0;
  for (let x = 0; x < s.length; x++){
    if (s[x] == "B")
      count++;
  }
  return count;
}
function countChar(s, t){
  let count = 0;
  for (let x = 0; x < s.length; x++){
    if (s[x] == t)
      count++;
  }
  return count;
}
```
