## Drum Kit

### 內容

1. 監聽鍵盤輸入，並呼叫`playSound`函式。
```javascript
window.addEventListener('keydown', playSound)
```
2. 選取keycode對應的data-key，`audio.currentTime`設定音頻播放位置(秒)，`key.classList.add`回傳class並新增class值。
```javascript
function playSound (e) {
    const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`)
    const key = document.querySelector(`.key[data-key="${e.keyCode}"]`)

    if (!audio) return
    audio.currentTime = 0
    audio.play()
    key.classList.add('playing')
  }
```
* `const`宣告不可變的常數。
* `document.querySelector(`audio[data-key="${e.keyCode}"]`)`，使用ES6模板字符串。

3. 對所有`class=key`設監聽`transitionend`，並執行`removeTransition`函式。針對`transform`這個property做判斷，當`transitionend`，移除`playing`這個`class`。

```javascript
function removeTransition (e) {
    if(e.propertyName !== 'transform') return
    this.classList.remove('playing')
  }
const keys = Array.from(document.querySelectorAll('.key'))
  keys.forEach(key => key.addEventListener('transitionend', removeTransition))
```
* ` Array.from`將資料轉成陣列。
* `key => key.addEventListener`箭頭函式，[Arrow Funciton](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Arrow_functions)。 