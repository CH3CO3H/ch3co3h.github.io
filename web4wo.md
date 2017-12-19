# Write Web Page for WeChat Offical account

做公众号消息的时候嫌第三方工具太垃圾? 自己写网页吧.

下面这条肯定是要有的.

```html
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=0">
```

另外还有以下几点: 

+ 不要使用 `<div>`, 使用 `<section>` 代替;
+ 不要使用`::before` `::after`;
+ 不要使用`position`;
+ `list-style-type` 无效;
+ `font-size` 和 `font-size` 无效, 很可能 font 类的属性都无效;
+ 对于图片, 我的做法是上传到微博相册;
+ 建议盒子的宽度用 vw, 高度自适应;

---

先这些吧, 以后有机会的话再补.