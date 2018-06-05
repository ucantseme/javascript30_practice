## Flex Panel Gallery 

### 內容

#### CSS

這裡運用到flexbox
[Flexbox](https://www.w3schools.com/Css/css3_flexbox.asp)

#### JS

不用手動關閉，點擊其他的就直接移除所有的`.open`。

```javascript
function toggleOpen () {
    panels.forEach(panel=>panel.classList.remove('open'))
    this.classList.toggle('open')
}
```