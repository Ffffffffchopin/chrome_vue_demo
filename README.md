
基于Vite4的Chrome Extension Manifest V3工程脚手架。

本项目架构实现了以下功能：

- 基于Vite 4.x搭建
- 基于Chrome Extension Manifest V3规范
- 集成Sass/Scss/Less/Stylus
- 集成Element Plus
- 集成mock.js、mockjs-fetch模拟请求
- 集成vue-router
- 将popup、content、background目录互相独立，便于团队协作开发维护
- 按照Chrome Extension最终生成目录要求配置Vite
- 封装fetch，满足popup、content script、background script跨域请求


## 安装项目
执行：
```
npm install
```
或
```
yarn
```

## 使用方法：开发环境

> ※注：为方便演示接口请求，本Demo使用了mock.js，也配置了反向代理。
> mock.js便于直接调试，使用前请修改src/api/index.js，将import '@/mock'前的注释去掉，保证mock.js的正确引入。
> 如使用反向代理，需要自行在本地搭建API服务，接口返回数据可参考src/mock.js中的数据。

执行：
```
npm run dev
```
或
```
yarn dev
```

## 使用方法：build项目

> ※注：
> 1. 执行build前一定检查是否取消mock.js，即确认src/api/index.js中，将import '@/mock'注释掉。这是因为mock.js使用window变量，而运行background script的Service Worker不支持window，将导致插件运行失败。
> 2. 执行build前一定检查src/popup/popup.vue代码中，注释掉import '@/content'。这段代码是用于方便在开发环境调试content script的，否则content script会被集成到popup页面中。

执行：
```
npm run build
```
或
```
yarn build
```

build完成后，打开Chrome浏览器，地址栏输入：
```
chrome://extensions/
```
进入扩展程序界面。

1. 开启右上角的“开发者模式”。
2. 点击左上角的“加载已解压的扩展程序”。
3. 选择项目工程中刚生成的build目录。

