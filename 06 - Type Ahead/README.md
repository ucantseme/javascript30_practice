## Type Ahead

### 內容

#### JS

1. 讀取json資料，這裡使用`fetch`取代傳統的`XMLHttpRequest`，並放入陣列中。
* [Fetch MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch)

2. 建立字串配對函式，使用[正規表達式](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Regular_Expressions)
* `g`全部搜尋
* `i`不分大小寫

3. 設定監聽事件
```javascript
searchInput.addEventListener('change', displayMatches);
searchInput.addEventListener('keyup', displayMatches);
```
`input`有三種事件`keydown`、`keyup`、`change`。
* `keydown`當按住不放時，會有重複觸發的功能。
* `change`會在焦點轉移時才執行。

4. 建立`displayMatches`函式，把匹配的對象顯示在網頁上。
```javascript
function displayMatches () {
  const matchArray = findMatches(this.value, cities)
  const html = matchArray.map(place => {
    const regex = new RegExp(this.value, 'gi');
    const cityName = place.city.replace(regex, `<span class="hl">${this.value}</span>`);
    const stateName = place.state.replace(regex, `<span class="hl">${this.value}</span>`);
    return `<li>
              <span class="name">${cityName}, ${stateName}</span>
            </li>`
  }).join('')
  suggestions.innerHTML = html
}
```
* 使用`join('')`，把陣列的內容全部連結在一起就不會有逗號了。

5. 最後讓數字加入逗號。

```javascript
function numberWithCommas(x) {
  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}
```
看不懂正規表達式，數字可用`Number.prototype.toLocaleString()`處理。
[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString)

```javascript
return (x * 1).toLocaleString()
```
* `x*1`是為了把字串轉數字。

並在`li`加入內容
```javascript
<span class="population">${numberWithCommas(place.population)}</span>
```