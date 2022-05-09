# 起飞~

------

[TOC]

###### 1.什么是节流和防抖，他们的应用市场有哪些

```js
// 防抖函数
function debounce(fn, wait) {
  let timer;
  return function () {
    let _this = this;
    let args = arguments;
    if (timer) {
      clearTimeout(timer);
    }
    timer = setTimeout(function () {
      fn.apply(_this, args);
    }, wait);
  };
}
// 使用
window.onresize = debounce(function () {
  console.log("resize");
}, 500);
//登录、发短信等按钮避免用户点击太快，以致于发送了多次请求，需要防抖
//调整浏览器窗口大小时，resize 次数过于频繁，造成计算过多，此时需要一次到位，就用到了防抖
//文本编辑器实时保存，当无任何更改操作一秒后进行保存




//节流函数
// 方式1: 使用时间戳
function throttle1(fn, wait) {
  let time = 0;
  return function () {
    let _this = this;
    let args = arguments;
    let now = Date.now();
    if (now - time > wait) {
      fn.apply(_this, args);
      time = now;
    }
  };
}
// 方式2: 使用定时器
function thorttle2(fn, wait) {
  let timer;
  return function () {
    let _this = this;
    let args = arguments;

    if (!timer) {
      timer = setTimeout(function () {
        timer = null;
        fn.apply(_this, args);
      }, wait);
    }
  };
}
//scroll 事件，每隔一秒计算一次位置信息等
//浏览器播放事件，每个一秒计算一次进度信息等
i//nput 框实时搜索并发送请求展示下拉列表，每隔一秒发送一次请求 (也可做防抖)
```



###### 2. 如何实现一个简单的 Promise

###### 3.JS中如何实现bind

###### 4.如何实现 promise.map，限制 promise 并发数

###### 5.如何实现类似 lodash.get 函数

###### 6.如何实现一个深拷贝 (cloneDeep)