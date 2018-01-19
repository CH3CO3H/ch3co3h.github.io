# Write Web Page for WeChat Offical account

做公众号消息的时候嫌第三方工具太垃圾? 自己写网页吧.

下面这条肯定是要有的.

```html
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=0">
```

另外还有以下几点:

+ 不要使用 `<div>`, 使用 `<section>` 代替;
+ 不要使用`::before` `::after`;
+ `position`无效;
+ `list-style-type` 无效;
+ % 会被转换为 px;

一些建议:

+ 对于图片, 我的做法是上传到微博相册;
+ 图片居中 `img {left:0;right:0;margin:auto;display:block;}`
+ 盒子的宽度用 vw, 高度自适应;
+ ul {margin-left: 1em;}

---

先这些吧, 以后有机会的话再补.
