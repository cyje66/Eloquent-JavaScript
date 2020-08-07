## 迴圈
印出下列圖案:
```
#
##
###
####
#####
######
#######
```
```
for (let line = "#"; line.length < 8; line += "#")
  console.log(line);
```
## Fizz-Buzz問題
列印出數字1~100，若該數可以被3整除，則印出Fizz；若可以被5整除，則印出Buzz；若可以被15整除，則印出FizzBuzz。
```
for (let n = 1; n <= 100; n++) {
  let output = "";
  if (n % 3 == 0) 
    output += "Fizz";
  if (n % 5 == 0) 
    output += "Buzz";
  console.log(output || n);
}
```

## Board game
寫出兩個符號交錯出現的棋盤。
```
let board = "";

// y控制列，y+1就多一列(橫)
for (let y = 0; y < 8; y++){
  // x控制行，x+1就多一行(直)
  for (let x = 0; x < 8; x++){
  	if ((x + y )% 2 == 0)
      board += "*";
    else if ((x + y) % 2 == 1)
      board += "#";
  }
  board += "\n"
}
console.log(board);
```
