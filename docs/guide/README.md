## 分页

### 初始化

```html
<ol class="pagination" id="pagelist"></ol>
```

```js
// 分页元素ID（必填）
var selector = '#pagelist';

// 分页配置
var pageOption = {
  // 每页显示数据条数（必填）
  limit: 5,
  // 数据总数（一般通过后端获取，必填）
  count: 162,
  // 当前页码（选填，默认为1）
  curr: 1,
  // 是否显示省略号（选填，默认显示）
  ellipsis: true,
  // 当前页前后两边可显示的页码个数（选填，默认为2）
  pageShow: 2,
  // 开启location.hash，并自定义hash值 （默认关闭）
  // 如果开启，在触发分页时，会自动对url追加：#!hash值={curr} 利用这个，可以在页面载入时就定位到指定页
  hash: false,
  // 页面加载后默认执行一次，然后当分页被切换时再次触发
  callback: function(obj) {
    // obj.curr：获取当前页码
    // obj.limit：获取每页显示数据条数
    // obj.isFirst：是否首次加载页面，一般用于初始加载的判断

    // 首次不执行
    if (!obj.isFirst) {
      // do something
    }
  }
};

// 初始化分页器
new Pagination(selector, pageOption);
```

### 使用场景

> 此分页器只负责分页本身的逻辑，具体的数据请求与渲染需要另外去完成

> 此分页器不仅能应用在一般的异步分页上，还可直接对一段已知数据进行分页展现，更可以取代传统的超链接分页

#### 前端分页

在`callback`里对总数据进行处理，然后取出当前页需要展示的数据即可

#### 后端分页

利用url上的页码参数，可以在页面载入时就定位到指定页码，并且可以同时请求后端指定页码下对应的数据
在`callback`回调函数里取得当前页码，可以使用`window.location.href`改变url，并将当前页码作为url参数，然后进行页面跳转
（例如`./test.html?page=`这种格式）

### 效果演示
![pagination](https://i.loli.net/2018/07/26/5b592fc2c630f.gif)

[pagination](https://csdoker.github.io/csdemos/pagination/)

## 轮播（Web）

### 初始化

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

### 使用场景

Web版轮播无自适应，在固定宽度和高度的容器元素中使用即可

### 效果演示
![carousel](https://i.loli.net/2018/08/10/5b6d05ea7e673.gif)

[carousel](https://csdoker.github.io/csdemos/carousel/pc/)

## 轮播（H5）

### 初始化

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

### 使用场景

> H5版只能在移动端环境使用，不支持PC Web环境，如果想直接在Web下测试效果，可以使用浏览器自带的设备模拟环境查看（比如Chrome下查看方式为：F12 -> Ctrl+Shift+M）

H5版轮播可自动适应屏幕宽度，在固定高宽的容器元素中也可使用。（考虑到用户使用及移动端布局的特点，取消了圆点和箭头，增加了触摸功能）

### 效果演示
![carousel-mobile](https://i.loli.net/2018/08/10/5b6d05e381d6b.gif)

[carousel-mobile](https://csdoker.github.io/csdemos/carousel/mobile/)

## 日历

### 初始化

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

### 使用场景

只支持PC端，暂时只支持日期选择，后续会考虑加入年份及月份选择

### 效果演示

[calendar](https://csdoker.github.io/csdemos/calendar/)
