## CSS+JS Clock

### 內容

#### css設置
* `transform-origin`設定中心點。
* `transform: rotate(90deg)`物件旋轉角度。
* `transition:`設定名稱、時間、速度曲線、延遲時間。
* `transition-timing-function`設定過度效果的速度曲線，可用google開發工具模擬。

#### js
1. 計算出轉動的角度，並且改變各自的`transform`角度。
```javascript
function setDate () {
      const now = new Date()
      const seconds = now.getSeconds()
      const secondsDegrees = (seconds / 60) * 360
      secondHand.style.transform = setDeg(secondsDegrees)

      const mins = now.getMinutes()
      const minsDegrees = (mins / 60) * 360
      minHand.style.transform = setDeg(minsDegrees)

      const hours = now.getHours()
      const hoursDegrees = (hours / 12) * 360
      hourHand.style.transform = setDeg(hoursDegrees)
    }
```
* `new Date()`取得時間點
>now.getSeconds()秒
>now.getMinutes()分
>now.getHours()時

2. 使用`setInterval`來執行函式
```javascript
setInterval(setDate,1000)
```
* `setInterval(function, milliseconds, param1, param2, ...)`直到`clearInterval()`才停止。

3. 解決在0度時，角度變化異常的狀況
```javascript
if(deg==0){
    document.querySelector('.hand').style.transition = 'all 0s'
```
* 改變transition設定，由於前面CSS把時鐘調整90度，所以判定0度時改變。  