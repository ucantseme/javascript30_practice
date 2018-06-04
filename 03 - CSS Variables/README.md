##  CSS Variables

### 內容

#### CSS
設定全域變數
```css
:root{
      --base: #ffc600;
      --blur: 10px;
      --spacing: 10px;
    }
```
使用變數
```css
img{
      background-color: var(--base);
      padding: var(--spacing);
      filter: blur(var(--blur));
    }
```
* [css filter濾鏡](https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter)

#### js
1. 選取所有`input`，用`forEach`設置監聽事件及執行函式。
```javascript
const inputs = document.querySelectorAll('.controls input')
function handleUpdate () {
      const suffix = this.dataset.sizing || ''
      document.documentElement.style.setProperty(`--${this.name}`,this.value + suffix)
    }
inputs.forEach(input => input.addEventListener('change', handleUpdate))
``` 
* `document.querySelectorAll`回傳的是NodeList不等於Array，需要用`Array.from`轉陣列。
* `data-keyname`HTML5的自訂義屬性，取值使用`dataset.keyname`。