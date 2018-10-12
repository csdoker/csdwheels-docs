### 分页

#### 初始化

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

#### 使用场景

> 此分页器只负责分页本身的逻辑，具体的数据请求与渲染需要另外去完成

> 此分页器不仅能应用在一般的异步分页上，还可直接对一段已知数据进行分页展现，更可以取代传统的超链接分页

##### 前端分页

在`callback`里对总数据进行处理，然后取出当前页需要展示的数据即可

##### 后端分页

利用url上的页码参数，可以在页面载入时就定位到指定页码，并且可以同时请求后端指定页码下对应的数据
在`callback`回调函数里取得当前页码，可以使用`window.location.href`改变url，并将当前页码作为url参数，然后进行页面跳转
（例如`./test.html?page=`这种格式）

#### 效果演示
![pagination](https://i.loli.net/2018/07/26/5b592fc2c630f.gif)

[pagination](https://csdoker.github.io/csdemos/pagination/)
