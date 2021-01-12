# You-Dont-Know-JS

### setTimeout loop

```javascript
var array = [1, 2, 3, 4, 5]
for(var i = 0; i < array.length; i++) {
  setTimeout(() => {
    console.log(array[i])
  }, 1000);
} 
// i = 5
```

為什麼他會是 5呢？ 因為setTimeout是一個callback fn 所以當loop完結束後，它才會去run，所以那個會是5了。而且還使用了var 這個 global variables. 
要怎樣 解決這個問題？

## Solution
* 最簡單的就是，換去 let variable就好了
* 可以做一個 function 被 call 在 iteration loop裡，那樣就是 loop的時候，馬上trigger這個function了。所以，i已經被assign了

```javascript
var array = [1, 2, 3, 4, 5]
for(var i = 0; i < array.length; i++) {
  delay(i)
}
function delay(i) {
  setTimeout(() => {
    console.log(array[i])
  }, 1000);
}
```
