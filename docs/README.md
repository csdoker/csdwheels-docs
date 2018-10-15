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
