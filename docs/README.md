# csdwheels

日常工作中经常会发现有大量业务逻辑是重复的，而用别人的插件和轮子也不能完美解决一些定制化的需求，所以我抽取出来了这套插件库，希望能让大家提升工作效率，少加班~

> 项目插件使用 ES5 语法及 UMD 规范封装，部分插件提供 ES6 及 Vue 版本（ES5版本只支持 script 标签的引入方式，ES6版本支持直接 import 导入）

[![Build Status](https://travis-ci.org/csdoker/csdwheels.svg?branch=master)](https://travis-ci.org/csdoker/csdwheels) [![npm](https://img.shields.io/npm/v/csdwheels.svg?style=flat-square)](https://www.npmjs.com/package/csdwheels) [![npm](https://img.shields.io/npm/dt/csdwheels.svg?style=flat-square)](https://www.npmjs.com/package/csdwheels) [![npm](https://img.shields.io/npm/l/csdwheels.svg?style=flat-square)](https://www.npmjs.com/package/csdwheels)

源码：[csdwheels](https://github.com/csdoker/csdwheels)

文档：[csdwheels-docs](https://csdoker.github.io/csdwheels-docs)

> 本套插件的[Vue版本](https://github.com/csdoker/vue-wheels)

## 版本说明

- ES5：`src/es5`文件下为ES5版本源码，ES5语法 + UMD（dist文件下为打包压缩后的代码）
- ES6：`src/es6`文件下为ES6版本源码，打包后支持ES5语法 + UMD + ES6的导入方式（dist-es6文件下为打包压缩后的代码）

## 安装插件

> npm install csdwheels -D

## 引入方式

### ES5 传统引入方式

在`dist`文件目录下，找到某个插件的css、js文件，然后将它们引入HTML文档中，并添加插件的DOM结构：
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="author" content="csdoker">
  <title>pagination</title>
  <link rel="stylesheet" href="pagination.min.css">
</head>
<body>
  <ol class="pagination" id="pagelist"></ol>
  <script type="text/javascript" src="pagination.min.js"></script>
</body>
</html>
```

### ES6 模块化引入

> ES6版本使用之前必须先使用命令安装插件的npm包

因为样式已打包进`dist-es6`目录下的源码中，所以只需要添加插件的DOM结构，然后在你的JS文件中使用`import`引入插件即可：
```html
<html>
<head>
  <meta charset="UTF-8">
  <meta name="author" content="csdoker">
  <title>pagination</title>
</head>
<body>
  <ol class="pagination" id="pagelist"></ol>
  <script src="./test.js"></script>
</body>
</html>
```

```javascript
// 安装npm包后，直接引入对应的插件
import { Pagination } from 'csdwheels';
```

### 轮播（Web）

#### 初始化

```html
<div class="carousel-container" id="carousel"></div>
```

```js
// 轮播元素ID（必填）
var selector = '#carousel';

// 轮播设置
var carouselOption = {
  // 轮播宽度（必填，一般和图片宽度保持一致）
  carouselWidth: 600,
  // 轮播高度（必填，一般和图片高度保持一致）
  carouselHeight: 400,
  // 轮播图片列表（必填，不填你显示什么。。）
  carouselImages: [
    'https://i.loli.net/2018/08/04/5b657fef3a46c.jpg',
    'https://i.loli.net/2018/08/04/5b657fef509c9.jpg',
    'https://i.loli.net/2018/08/04/5b657fef51617.jpg',
    'https://i.loli.net/2018/08/04/5b657fef530a1.jpg',
    'https://i.loli.net/2018/08/04/5b657fef52441.jpg'
  ],
  // 是否显示轮播箭头（选填，默认显示）
  showCarouselArrow: true,
  // 是否显示轮播圆点 （选填，默认显示）
  showCarouselDot: true,
  // 轮播自动播放间隔（选填，默认3000ms）
  carouselInterval: 3000,
  // 轮播动画总时间（选填，默认150ms）
  carouselAnimateTime: 150,
  // 轮播动画间隔（选填，默认10ms）
  carouselAnimateInterval: 10
  // 通过 轮播宽度 / (轮播动画总时间 / 轮播动画间隔) 这个公式可以计算出每次轮播动画的移动速度
};

// 初始化轮播
new Carousel(selector, carouselOption);
```

#### 使用场景

Web版轮播无自适应，在固定宽度和高度的容器元素中使用即可

#### 效果演示
![carousel](https://i.loli.net/2018/08/10/5b6d05ea7e673.gif)

[carousel](https://csdoker.github.io/csdemos/carousel/pc/)

### 轮播（H5）

#### 初始化

```html
<head>
  <!-- 在H5页面的head标签中需要设置viewport -->
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">
</head>

<div class="carousel-mobile-container" id="carousel"></div>
```

```js
// 轮播元素ID（必填）
var selector = '#carousel';

// 轮播设置
var carouselOption = {
  // 轮播图片列表（必填）
  carouselImages: [
    'https://i.loli.net/2018/08/04/5b657fef3a46c.jpg',
    'https://i.loli.net/2018/08/04/5b657fef509c9.jpg',
    'https://i.loli.net/2018/08/04/5b657fef51617.jpg',
    'https://i.loli.net/2018/08/04/5b657fef530a1.jpg',
    'https://i.loli.net/2018/08/04/5b657fef52441.jpg'
  ],
  // 轮播自动播放间隔（选填，默认3000ms）
  carouselInterval: 3000,
  // 轮播滑动一次的时间
  carouselDuration: 300
};

// 初始化轮播
new CarouselMobile(selector, carouselOption);
```

#### 使用场景

> H5版只能在移动端环境使用，不支持PC Web环境，如果想直接在Web下测试效果，可以使用浏览器自带的设备模拟环境查看（比如Chrome下查看方式为：F12 -> Ctrl+Shift+M）

H5版轮播可自动适应屏幕宽度，在固定高宽的容器元素中也可使用。（考虑到用户使用及移动端布局的特点，取消了圆点和箭头，增加了触摸功能）

#### 效果演示
![carousel-mobile](https://i.loli.net/2018/08/10/5b6d05e381d6b.gif)

[carousel-mobile](https://csdoker.github.io/csdemos/carousel/mobile/)

### 日历

#### 初始化

```html
<div class="calendar" id="calendar"></div>
```

```js
// 日历元素ID（必填）
var selector = '#calendar';

// 日历设置
var calendarOption = {
  // 日期，支持new Date格式、字符串格式（选填，默认为当前时间）
  time: '1970-1-1'
  // time: new Date('1970-1-1');
};

// 初始化日历
new Calendar('#calendar', calendarOption);

// 监听日历点击事件，获取选中日期的值
calendar.on('click', function(calendarTime) {
    console.log(calendarTime);
});
```

#### 使用场景

只支持PC端，暂时只支持日期选择，后续会考虑加入年份及月份选择

#### 效果演示

[calendar](https://csdoker.github.io/csdemos/calendar/)
