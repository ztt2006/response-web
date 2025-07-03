## 一、项目开发流程

TIP

以下是本次项目的开发流程（针对企业真实的大型项目开发，接到项目后，就要开会一起讨论，定项目的功能设计和开发流程、进度等）

### 1、第一步：我们需要分析整个项目有哪些具体的功能

TIP

- 响应式功能 、主题皮肤切换功能
- 大量 JavaScript 特效
  - 页面加载进度条、滑动二级下拉菜单
  - 垂直二级伸缩菜单、响应式二级菜单、抽屉式菜单
  - 吸顶盒菜单、右侧悬浮菜单
  - 数字动画、带左右按扭的轮播图、Tab 选项卡切换特效
  - 滑块跟随鼠标导航、导航吸顶盒效果
  - 楼梯式导航特效、点击弹出显示大图轮播
  - 页面滚动加载动画、点击返回页面顶部
- 大量 CSS3 动画
  - 淡入淡出动画、鼠标悬停动画
  - 3D 翻转动画、滑动扫光效果、复杂的过渡动画

### 2、第二步：针对项目的功能，选择采用什么样的实现方案

TIP

- 针对响应式功能，我选择自己手写响应式栅格系统来实现 （手写 `media.css`）
- 针对主题皮肤的切换功能，我选择采用 原生 JS + CSS 手动实现
- 针对项目中的 JS 动画特效，播图我们选用 Swiper 插件来实现，其余动画均采用手写原生 JS 实现
- CSS3 动画能用 `animate.css` 库实现的都用他实现，其它的均自己手写。

### 3、第三步：开始项目架构的搭建

TIP

由于受限于现阶段所学知识，该项目只是静态页面开发 + JavaScript 效果，暂时不涉及 前端框架相关内容，整个项目架构的搭建同时整合了一线互联网大厂项目最佳实践 和 规范。

> 为我们先一步建立企业项目开发思维流程 和 认知。

## 二、项目开发架构搭建

TIP

在正式进入项目具体功能开发前，我们需要先搭建好项目架构。本项目架构搭建，主要完成以下内容

- 创建项目的目录结构
- 重置默认样式
- 设置项目通用字体样式
- 定制主题皮肤
- 准备项目所需要的图片素材
- 实现响应式栅格系统
- 准备好项目中用到 iconfont 图标
- 使用 git 管理项目

### 1、创建项目的目录结构

TIP

- 新建项目文件夹 `response-web`
- 在 `response-web` 中新建 `css`、`js`、`images` 文件夹，分别用来存放 CSS、JS 文件和图片
- 在 `css` 文件夹中新建 `reset.css` 、`global.css`、 `index.css` 文件，分别用来存放重置默认样式、全局通用样式，首页样式

```js
response-web  // 项目文件夹 - 用来存文本项目所有内容
├─ css  // css文件夹，用来存放 css 文件
│  ├─ global.css  //  全局通用样式
│  ├─ index.css  // 项目首页样式
│  └─ reset.css  // 重置默认样式
├─ images // images 文件夹，用来存放项目图片素材
├─ index.html  // 项目首页
└─ js  // js 文件夹，用来存放 js 文件
```

### 2、重置默认样式

TIP

在 `css/reset.css` 文件中，添加如下 css，用来重置 html 标签的默认样式

<details class="custom-block details" style="display: block; border-radius: 2px; margin: 1.6em 0px; padding: 1.6em; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Oxygen, Ubuntu, Cantarell, &quot;Fira Sans&quot;, &quot;Droid Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="outline: none; cursor: pointer; color: rgb(62, 175, 124);">点击查看完整源代码</summary><div class="language-css extra-class" style="position: relative; background-color: rgb(40, 44, 52); border-radius: 6px;"><pre class="language-css" style="color: rgb(204, 204, 204); background: transparent; font-family: Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace; font-size: 1em; text-align: left; white-space: pre; word-spacing: normal; word-break: normal; overflow-wrap: normal; line-height: 1.4; tab-size: 4; hyphens: none; padding: 1.25rem 1.5rem; margin: 0.85rem 0px; overflow: auto; border-radius: 6px; position: relative; z-index: 1;"><code style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(255, 255, 255); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span class="token atrule" style="color: rgb(204, 153, 205);"><span class="token rule"></span><span class="token string" style="color: rgb(126, 198, 153);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token function" style="color: rgb(240, 141, 73);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></code></pre></div></details>

关于标签默认样式及清除相关内容，可以参考博客 [标签默认博客地 (opens new window)](https://www.arryblog.com/guide/project/#三、标签默认样式及清除)[(opens new window) (opens new window)](https://www.arryblog.com/guide/project/#三、标签默认样式及清除)👆 中如下截图内容

![image-20220815153351605](https://www.arryblog.com/assets/img/image-20220815153351605.d1880d52.png)

### 3、设置通用字体样式

TIP

通过对设计稿的分析，我们可以了解页面字体通用样式

- 页面中大部分字体为 `16px`
- 行间距为字体大小的 `1.5 倍` （每个公司要求不一样，在实际开发中，以公司规范定为主）
- 字体类型主要是**微软雅黑**
- 字体颜色主要以`#000` 黑色为主

> 通过以上数据最后得到如下代码，添加到 `./css/global.css` 文件中，作为全局通用样式

```css
/* 项目通用字体样式 */
body {
  /* 字体大小： 16px  
    行高：为字体的 1.5倍 
    字体类型：微软雅黑 */
  font: 16px/1.5 Microsoft YaHei;
  color: #000; /* 字体颜色 */
}
```

### 4、定制主题皮肤

TIP

通过对设计稿的用色分析，可以定制出网站的皮肤主题。

> 以下是本项目三种不同皮肤主题的颜色（这部分主要由设计师来定）

![image-20250112171414974](https://www.arryblog.com/assets/img/image-20250112171414974.c0721dfe.png)

主题二和主题三，在这个项目中，只是主色调最深的色不一样，其它都一样

![image-20250112153206435](https://www.arryblog.com/assets/img/image-20250112153206435.6ff452f5.png)

注：

通过给出的三套皮肤色，我们可以定义三套皮肤主题。

在`css` 文件夹中，新建 `skin-theme.css` 文件，用来保存当前网站的皮肤主题

> 通过更新 html 标签上自定义属性 `data-theme` 的值来切换到不同主题

```css
/* 清绿色 turquoise 默认主题 */
:root,
html[data-theme="turquoise"] {
  /* 主色调 */
  --primary--color: #1ec28b; /* 主体色 */
  --light-gray-color: #f4f4f6; /* 浅灰色 */
  --white-color: #fff; /* 白色 */

  /* 字体色 */
  --font-black-color: #000; /* 黑色 */
  --font-dark-grey-color: #666; /* 深灰色 */
  --font-red-color: #ff0000; /* 红色 */
  --font-white-color: #fff; /* 白色 */

  /* 边框色 */
  --border-dark-grey-color: rgba(28, 28, 27, 0.22); /* 深灰色边框 */

  /* 辅助色 */
  --sub-dark-red-color: #ff6347; /* 深红色 */
  --sub-deep-orange-color: #ff8900; /* 深橘红色 */

  /* 网站底部色 */
  --footer-bg-color1: #2e2e2e; /* 网站底部背景色 */
  --footer-bg-color2: #212121; /* 网站底部背景色 */
  --footer-font-color: #d6d6d6; /* 网站底部背景色 */
}

/* 深黄色 #ffd336 */
html[data-theme="yellow"] {
  /* 主色调 */
  --primary--color: #ffd336; /* 主体色 */
  --light-gray-color: #f4f4f6; /* 浅灰色 */
  --white-color: #fff; /* 白色 */

  /* 字体色 */
  --font-black-color: #000; /* 黑色 */
  --font-dark-grey-color: #666; /* 深灰色 */
  --font-red-color: #ff0000; /* 红色 */
  --font-white-color: #fff; /* 白色 */

  /* 边框色 */
  --border-dark-grey-color: rgba(28, 28, 27, 0.22); /* 深灰色边框 */

  /* 辅助色 */
  --sub-dark-red-color: #ff6347; /* 深红色 */
  --sub-deep-orange-color: #ff8900; /* 深橘红色 */

  /* 网站底部色 */
  --footer-bg-color1: #2e2e2e; /* 网站底部背景色 */
  --footer-bg-color2: #212121; /* 网站底部背景色 */
  --footer-font-color: #d6d6d6; /* 网站底部背景色 */
}

/* 深红色 */
html[data-theme="red"] {
  /* 主色调 */
  --primary--color: #ff383f; /* 主体色 */
  --light-gray-color: #f4f4f6; /* 浅灰色 */
  --white-color: #fff; /* 白色 */

  /* 字体色 */
  --font-black-color: #000; /* 黑色 */
  --font-dark-grey-color: #666; /* 深灰色 */
  --font-red-color: #ff0000; /* 红色 */
  --font-white-color: #fff; /* 白色 */

  /* 边框色 */
  --border-dark-grey-color: rgba(28, 28, 27, 0.22); /* 深灰色边框 */

  /* 辅助色 */
  --sub-dark-red-color: #ff6347; /* 深红色 */
  --sub-deep-orange-color: #ff8900; /* 深橘红色 */

  /* 网站底部色 */
  --footer-bg-color1: #2e2e2e; /* 网站底部背景色 */
  --footer-bg-color2: #212121; /* 网站底部背景色 */
  --footer-font-color: #d6d6d6; /* 网站底部背景色 */
}
```

### 4.1、使用皮肤主题

TIP

- 在 `index.html` 页面中引用 `skin-theme.css` 文件
- 然后，使用 `skin-theme.css` 文件中定义的主题皮肤色

```html
<link rel="stylesheet" href="./css/skin-theme.css" />
<style>
    .box {
        width: 200px;
        height: 100px;
         /* 背景颜色使用css变量，在不同的皮肤主题下，背景颜色不一样 */
        background-color: var(--primary-color);
    }
</style>
</head>
<body>
    <div class="box">我是一个长方形，不同皮肤主题下，我的背景颜色不一样。</div>
</body>
```

![image-20250112174050053](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAANQAAAByCAIAAACk+Wi8AAAPVUlEQVR4nO2dTWga3RrHn3sNtY0YbExubvGiELoL3iK8vLtMkGQh3RWhCxe6cCW4vG4V3XqXgqssdOGiIN2FLJQQs3spSBF3peDA0JtqUlE0tWR472K+Z87ojDE5ad/nt9JRZ86c+Z9znvPxP/7tzz//BAShwd9pJwD564LiQ6iB4kOogeJDqIHiQ6iB4kOosWY8FLj478OnA/nl6e3/R3cEaz6EGig+hBooPiLjSS4zaIxpJ+MXZ4H4+EaVZTIskxk0xtBvD5jmTDhY6T1M+uYmrDrp39Pp3U/3g9PCH7M7naQ3yrX5FSXo/hlPcplR1/QjQQYsk2G1NzWrLF9KCR0O6DbZ1Kn4OhzzteIO4bX8pF8deC9KLBPZaR06ib8i4SkXN/aWS6SBfvtboQMAVyc9VyJg8qXxJFfg3xIv2hsx54563LVtegXH0RvvRWHWPXQaf95vD6K1KfFnybRfTE9vxJR+JNOuRbdihG9UuULH6rfDMV8+dFvJXB5b+LKSPNusZ7NbR27oNtl3y52AAEl8e4f+1iEIuXBB+NyxHXDli2u7mcvKS+3NaOWoMJ7kCqurA3qjaG2aTPsTMGJKo99sarrbZFOn69n0c+nAvId9lhlqD6xns1tHoa1WiG9UuYugLx9yAMwqmbEvu3Xk1l5CdcQOjqO4/8h4uDdiSj9Mznkri8McvlHlOM3ZhsYvGe53lVWGAZL4zNjefALX8jtnoujXf+P0kjGt/Dxv7aXMhPEkVxqGY75EAAA2yhE2VZ1fh6kQcjyy0yqqS4jmYXebbApMipAlZpXM5fHqn9msUoJycWuV5wx6NflmbCh6I+bc8Q/ST/V1f4EtEM+5AKP4/jfJZa7O5Lcd7qym+Vwnr3BMKP0AcP81X2/ElIbqK+4d+stNNlqFBfc8nuQKV2dBb73ot5w1y9BtXh7LmTCe5N5D2sbDMINvVC+PAaC3sTev0ZyZN77r2exz8ifm9K9/gM8tJX5akBQWjsF2aKsVAoC5sc1ijOL7pytfdOUBxGY3qNLWwty8z5pPKG1S1DKrZC4/x3z5kEPUX4Y3qWz4RpUrgLde9OcXX4T/wgH4lk/k3qG/JbwaT3KFq930CrTebX6DA2+4c7Xoi85E0Z8w/ZRv2Lzudmirpbx7qJhvHh3+K4CQod0m++GBYj4hLPOYtTt7h/7WyxGTYUkBtUkINQdyEZKDKlWMqG4WhIpBaHd6I6Y0vEN0r9BvDz683EpsToTgu9tkU5ytps2czlU0oxe0Nua714APFovvrCblb9Bbj6/tws2XMey5hZjak83yAEoL2DI7i9uVL0qvhRbQcgLDse3dWv+zqtNNJrDRKroaVZbxbWe5vtyBMETQOnT5e8t1tIGEkuYb6Y2gZr5R5bgDuRqWOxx8o8oWOuvZrH+p3oaGfntQguf5AIA0lrF36K+3B9HMlVk5J405mGgo6K3H1060XSUJvlHlCj5CTx8AAL5XMlfq9l2dyYTcM4UgPk3ooD0X7wtOuWu+8V6oh4RbsjU0sJ7NbknNumVChp4NGbmS8x+BLhyZVTKXsLAq6s2OAZKbhry75s/gyVsLYuo2uYJvpxV3Sm8HX35frs9riHkkhHir22SZDPlJaw4uaHOcifSMeT95pa1K++1vhY6nHFeLWx3zPZXb9357EK3Bsv16gvjk0ME41OJ4FVwvlDgIeutFObnyI1dXBtBtsu82rReC+8aZSHsWjst0Pw0BPL9Zaitvuc66743+qLr67zbZFOcpL5HY8SRXuIK5Vcjeob91OKtkOOZ6p3Vo+wpKZyKwUQ8Oos01uR6V9KTLKLGu0cZ8/MfONBnzXvwxO1pmfMDW9FpvFK1NATxlsaDwjapqvLs3KXQ0T+6sxjGqkXGG7oRVYKMcGabMBvEBoDdKnUI45iKMKl//gKB20KE3O4YnL8yLuxScbezZrRKknoqFcutMFP1LjwqFN8WKZzu0Vd8cC9NF3SYbrU2TaW1Nds2TwyThiYee7nOXS814We1wiG1xMu3znXPv2q58yCFESLsHYh51Pw0B4INqOMBO83+/9NuDaOdZPe6vbw6imQGhmRhPcqUhBL1pawnufhqGYz6TSnRWyVweR5TGV318cdPvduWLS8yLKChhuohxnIH/2JnuHmzJ77dDW+VrNpq5Ig5W969/QMStv9nxJFcaJtP+PYC9N95cYdS13TtZJL7dTYc8xtEScu2N96LAVTb9ic3bz+B5K80mpU495azjXYFlgt56/E7ZtzqGqcwQ1JOEoa3Wy0muwBbUYbg8CkjuRc5OatNw7LnykXCzRYJMhXg/HPO1jCLuzY7BU75z/3chi8v8+PtFx/M2Lr8VuoCecnEDmmxKHwLyHzvTpEqpAMqAq1iQ3K58esQQS/U8iOJT5l485ThsB6QRRZCuVFyrZFgGACI7eVBmfvbckC+63jZZqQ+vH6CGO00v2qP/6eaMOOnkduWLrvx4ksuwZ+ApF50fClegk4tu9inorSufzirCzRqv2B6kTk2HJ8j1x6rZOzQbzrzlOgAHAELORNx5AFWD5s8LD+XQ31JyZmMPAMbfL8CbDsj96PVk5BujDLhKBDZa2UmuwHI2nu/fjKZxuyuZ9TObD4IyyPyQV70Dmt6YbaRA0OTn5o9APbAlVu3il1/8MX8CWtTl6mIn40rmFYgPQayAy+iRRwSKD6EGig+hBooPoQaK79ei22SZ5t2sJw+HNfFJ1qGfDhsGqH57YHAkaecPyagcNL3RSj1Nto1a/fYgdbqe/X3pZdgPjLXpte2QO2l0bCgY1tBGdspwSfITrWezz+G9DYPMEoPSSxmgxHF8zQyHOBOw1CiXvGRfXtW8aCGZYUTNcXTgYc4nr4X5BpMzKL8aT0q1KQDIy08kdIN5SxiU7mkw1fo43zzHl2aQs98eRK/d8nO14IoQVo/dxTlhelr1qiRtwpSZVqMbTchxgktNmDnUH5eernpehOCQuNk3H4pXLwIi+wAlHeuyV3X+qzP9Ij9pltlKxs4zKK0E4zjfguk1Pfq1r8qNTTUFLiLfAf+Fg+TBo2gI5hmgVE9IWjU0O6k9Ua+d7rcH0Q4AqBwMAELBU86j0ZxuVmNqqJM0hGPiC3FhtlTUxVURYvLmzbRqJ5T5RtWy8u7DoLQYovgCG63ihvaQ6dpGCaVu77cH0WttM9FhxUbZal7cAV3zZMEAlSadptu8/BzzzbNEKI3Xela5nGIzgPH3i876vrLmb567Ue+NCDiTncuTnisRmJ3Upsn01rZm+b6Un8Jq5NIQCItZhG+qLAGmmW/RoLRy7Ho4TCHWfJrs7jbZ1JwTcONc5nL+CkpLuG0boPpt41m+fzj17Ea+NcZaufjWJBGsZ7P+Vhw0NV/AlQ1yKfXC/chOXvm51ZoPAACcr2Pr0U+zBMyOg946cZVab8Scg7j4tzdiSqBa00CyEptc17JBaeWsRnwk39T4VnwhBYuLTvIsnX1WKnBMZ0UGGSLzDVAKTxNFB/RGTGH0Qr9KRedIciYUF7C5WUkpEgCwaKGAUnlPGQAQop2IN6t8erOf3bLnijLhHg1Ki1mB+Mh20XDEY+80vrVttzNffLpf5aKZm1VFvlYNUFrHmlgJBTbqsUG0OhEextfrKYASyy7qM2rjENL2Gmcl1pBv8oos1dIsofQePv1YtXXri7FkULJt+LqTgQjArMOlj5+EDHJq7CRyR2w8yZ0CCOvY4JnlxDuO4v6j3ogpsBdLNsF2DVAAQOxwAAhjTLXLUvspMSXmw0CaXoi2g2L/XsROzELv6TCls+rpWvmI+o11g5LLtuHLKibik7ZrWZxWAJAjjFeEj/iPnakd8QGAsDLRkRPWS9sOge0aoBadLe1hzr+nQy5Q+R4EjglVl4yqFyIlZv7omk7KH5ps6tRTLvoTwDeqLHfgU5nZn7xwg6rnLjDPZquJ+WwblO6pj7iyDofkphHbL8EiuVbJcMfgycZu5lhNydzZykCAYIDiLoLk3q5CYKMVBwD4avjEYs0nY94kaXfxAQCA3w79iUPVDiEBELccuObPgo4FaTZg3ErBQqmevwXC3VmJ+HqzYxgeVx3loNx+8Y0qy3RAdn4cCTV586578Cw24Jj/1tQApa9CiPBfOIBNzSE7NR+A2WiIRPJAeiXIS7W/DLQHubZ7HwDgtnE+hM76x7HLfodDzMDVl+olWYX4BCtXGr5Fa1NpkIXQ75u3pYEVljLgWDJAXZt0ONSMv1+orHoCdmo+ZZ+Di6AvHwLpxa3RDyCYauEa0kV/XtgCAbzlN2t7If+r9iDa8ZTTkCqwF+pdHDYd4YVB4UM5mCyzaMcCDYYBWwBIpnfg1PO26NgGcdc6JjPvgksbiGwYcGwaoPpg0uHQdfQiO3mLKR/fftbtNySdKhzzpV+qj6+9Lu6cZDimBlLQxn/sTMPB59sBR7fJRk/l1kPYiEMM7FpFpyYgc7veRlh9h8OAud2TCo/Cw2FlbvduBpzVY0yPttCq59k0+wbJX9NPeEhjbGsnmdlvRecHTY1INEwtnHayjI1AcGnQQIRQAw1EyCMCxYdQA8WHUAPFh1ADxYdQw1x8Wh/UrKLd2a7fHvxMf6+DPEas1nzO17EfKdmaNZ6UarC7Of8nCDIfy83uduh5Fq5OegAwqxRu9rNbicDPskMU8jghDDL/K/dvzeKfcMy7W7siT7jZ+8cZ5K+MJfeaMgWuTHmFXOLSmjv94wyCqDFrdsffLyz7ihFkKUyWVPU/3ZwBwOklw3nrcddX7ap6+U8/Hs+W38hPCFl8/McOhINw5tupb46jzbWWvKoem11kZRCb3d6kAM/2fQBCJ5ebmf53BYIsD0F8fON8mDxwvRDfOo7iWM8h9wGh2b3lwPs6AF8/ie+NNkr1H7092F8bIL8cxP9eiztBZdbS2ChNYj7JF33ff5KJ/EqsZGHBeFKqPSkX/fXYj9RPuYckQgVc1YJQYyW+XcU65SkXH8VWfMjPABqIkAcCDUTIIwLFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1ADxYdQA8WHUAPFh1CD8FcICPIwYM2HUAPFh1ADxYdQA8WHUAPFh1ADxYdQ4/8OK+xhRV71/AAAAABJRU5ErkJggg==)

### 4.2、皮肤主题切换原理

TIP

通过更新 html 标签上自定义属性 `data-theme` 的值来切换到不同主题

```html
<!-- 将 data-theme 的值更新为  red  、 yellow 、 turquoise 时，可以看到不同 -->
<html lang="en" data-theme="red">
  <!--  --->
</html>
```

`data-theme` 属性不同值的效果

| data-theme="red"                                             | data-theme="yellow"                                          | data-theme="turquoise"                                       |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| ![image-20250112180916343](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAANEAAABvCAIAAAD9mLK9AAAPOklEQVR4nO2dPWziyhbHj5+eWBQl3F1BEAiRyFIoEDRQQRqe0r8mdKTcctvtQgndbbd8JXTQvB49N7Er0oAoiIQWhLDAUXYdtCJueIU/x9jY5sN7d+/5KQUQY4/H/zlzZuacgVqv14AgPvKPn10A5G8Hag7xG9Qc4jeoOcRvUHOI3/yTeFf8108qBvJbw/7P+A7tHOI3qDnEb1BzJqTmkCkL0s8uxu+MreZ4oU9xDMUxZUECaV7mxqz84VT0s3w2Bes3j6WKwM2HSPuJZ/c6iVgfzvkDFej4SM0hU1/a/kuWAcUxFHlT7HTHxkmOIZZjqjdSXofTs0ImplxaPSCUbHx9pDj6oXBRtPyWFbVs6f50h7JZIc0/PQkAcLcQK4mQ3UHNITuKW15UrHMTOp+pBGyvEIukGi9sZ3lR3Py6NC93B23LryVza6U8Yp177CZzH51uZRNe6MefBLdHh9OzVHQ0Za4nLg7Wi+eZ26tiKxKA5Zia7XYCM6TmTi/WhQuQb/7F4uhYIFRJlegT5nr6nrwHUoU6UnPIbtOjN8R6d9BO5tYJqHOP9T88Snk5pnqj2ytdDdue8TNTJT+4vSq2ItFWIcoL/fjL+SwVjQGwU+bPd8VWRJWwcgnDJ16IRTLryObHYp177Nqcc6Rpwh5e6MffiLNVNw/auN9DWgqSfzofAgCBYB5W2rtiorQRFzC65mylVYvvUrINpObwsRpOzxIhALjP0lSvv91iGZArmn4olIwNg3jGyzHVA5uW4wp2ylxPDv+o2OkjZEutQ54z0iDqbbNbEOvchLasWLOlZ6kny3Nuw6g5vjlk7p61t0L8eUAca1JVOC23dQA4vp0T69xj1XjF04t1dkx1++Bwq1JzyN49Rxr50noX0+Oa5fh6olWC1BwO4dLtM9gCL/SvJwAg3p9u6xlZ+x729qr4xetVpVUXzm7UwrefVGGF0xCItgpR+SB7B8YBo+ZilVSpkgJQ+tZzg6QcK/GYdk5uW6pHwk6Z6x/pWSoaU2THjGxMCy/040/QyJfWKeeL8KtXgLPdC3l6sS4oxW0O2buT3AEkvhx/gmQjLNw5HVhMlNYJ2//yrl1EhUC0VdDfHdmf24YwkgDkelyOqe8++XOyy1Wz61xOL9aF93WOoax8ZBv3aAvWLUdzmAz+n7ETkM2A3LmIde6xuofDriPNy9/ftxLBpuxYL8dU79V9/7UV4a7LmHVM+nPHc+Zgm+aeB2q1Rhr5DH0CrZUEpwHZTa5dFXkAvZsr2J0lUEmV1NdyN+e6aOH0f08G//5hGD5bE7ovlD4KfYo7++/V67+1McGGU2zCVK2jN4H0FvQyt9Q3soh5oR9/S2pGVxtD8EKfehJur4rrnQYQ5GXn5a/wJRXSpwxOL9b5ebnL3Nk1b6vZAxvpRBr5DL0gRz8qvNCPP53d2AiuM2XujJ24sZItas8aQnOEW0Cegn8Xab+teGEoWx35TjyN7W+vii2173ZN1GUQs2bS1hEwuRrslLkGR8MjdiYAyeBGla1Gz5CPu9DQchx/OnsoZIrq2/IqttvodcOxUZF9qeWY4hjrB0x86NDDFBO5PDdshkjDKc0/PQm1bMaoaaM/d6N14tK83B3ATiN0QnOaW7A5VxILnd92H+MQaeRLWim1J21s+rAcU7OgS8n7QDGRqzlOrCy/VQFqf7jqEEdvwu27jaZjNPbLMdV7rWV3qACpOWTvYKvBOL1YFy7YKRPnVg+FC+9X0MYHofv8ebk7pjWrqcrIVFGKiSH9OV5ctJPpxgvPRjyP9F36c2K9O2gD1LJKsyDbovifJ6GWzeiH6/2yws5TVocgdJ+lqR4Dtj6KWO+NIJz+aDEJvOpCpEwUXOxMIJ+1v5fdHS918OHCF9Sswy7rJeEgLb8IRFv5eZnrl/OZijSmeiNI5kjHYDV6BrAYAipP/OZdPz4VvTqvzppTOtxkbvZuEp/NP6aiMdn7OUkqbXH5rQoA3w3jeddd+9GR5uXuopzPrPPBcpcpW0hfag4fqxBpXLor8PJbNZye2ZhMdspcT2i9hzV+7ty/ByqpUsVNGezYaOqbMwa8uGifJDUPFQLRVnZFdZk7S7sgrbpAfzbfrNQcPlaTufUpwGmqMWTrS28DDvs1/pNgTJqXOeYacutCaZ0IxSKpBgziUxFAGv3QeiKx3hvVssXGj8djLoN6ptpjKI6hvsKXQqYSkJ2hYvmFpTjj2qI2e2dtltjFoB0+v9H/JdZ7o1rcSp3LMcUx1z/SMwsHX+xM3HbcexFOzwqlteFvQwpS50UwlERqDhmqN6plS+ss3X4amh4fLy7ayffk7Yh1jr0DZWYeIFBJ5aDnbeHVZOf0hZFaNgOBkDoBCOoFSvSUoTgAoB9SoC/LnAYgVarEx5Q6CDfPJ8NeS37ekL61ni1780AlVaqkpOaQoZ6hli3dfGfvID0rGDVkWhqKNPL6f9mpfLObV5yXeyPb+QVra3FoTi/spiFHbwJAEkCuGfpzCsDQfa1T8kO5WBf0mrk/BQCp8wKNy5A2Ir5N0p84faJUJXRfKDaHLPXm9vlSRH6rxzhh82qjL+hzwn5edQ+IAZZnHJw8+0dgnJlSDLlycJDfviisyPGADhIZJ7yX5hDEFRibjvxcUHOI36DmEL9BzSF+g5r7XViOKW68XxqHTzhpTs2++eXwkEMkzcsbs9m80Kec8mgMSShi/aDz4Z5znaR5uTe6vYrtHOTsJ05rX4Ho5+Rm9oPORoQq/ZCFa6uUnNur4hcYesgx2WEOeaccIl5ctJPJFjFXJXVehFp8ewyVHVocvBYz7BTBtTETFoska9ykeS6vjticQf+W1Pw6aAOAFgCiYpqE2yHH5xiToM7rrcVEznD/Fug3Js3L3ZWWyGOVYWAOopSjtfbJQiDwmkOkR/cLlNxy5IqWvrWeoU1E4EUa+UwFzHlft1faSy0Q0iIOfluIgzFewxQDp5yQfiiU1imlej+b60pWpDmoTl75/UxedIccn2Ngu/ZlxhxZqt9km2he9Gf1Fb96hWTyL2Htt+UQGZ6W+vjZxSBvjEyW5uXuAgAM2QAA8hqAfh5i0da09tDesEAE4bTyQgl7VrMhlQAFpXiKPSa+qaaJEMt3chaFXeS2mSPk+Dhg0lzovlC6Jz+yDSFUMds5oi9Q7Ydt8PoBMfVBLnKILq1Osxxf/0jPtqUX6D2U0c7psfsgdV6E2w/68qdbOwcAELpJCtcLsZIIsYtBO5lrBYiYeLU+5VjfxypYhJPIRxri7G0r32WOz2Fxnw9hi6WdI2p5OaZ6W07w+ueQaW8PVHRFwHMOkTTfPEvn+6h2Qn8SJFIlZ7T67G+viutCBgg7F/p4FYn3jH0x/ZDSv+7WzgEAQPE8fdv9xiagM4k08pbhYWKdm4ASRSfWuUdjaKBVyq3NdV3n+ByWfTVnlXEkqe1LTZp3Okn5slj+ysa5xYFyTCzZnkOkc5MoxUCsc2w9aI4TMflDxUSpZfMvA3pLAACnNXvdVLc5AJBdGrpxpf+39aHY8pZYZMMRc3wc2Etz1mmVYbrm7TRndCBQTJVuPvTjXaZ1KGfWbQ4RmeulmJzQfT5d7vabil+1agPofqrT6I90Nqz2mnh+pDbqTQuFMsREyY324kbse7p1Z1zl+HjOmdolBwfAbvMRs28k10uRyMjQhlRSczjqghw3BrTrMscimXVErHMs9bJjP+s1hwgALMcQAPIk0eD66/zGsiT28zjEwIIcc3i/F2Vc4rjdTrVnSnIzdeXEQ3Cf41PxnDPlig3NaTMdjkUEAM17sKp/Xly0AcreyhO6LxTpIRufBncIOPOaQ+R0tlyNm3QuoxUw5BDITCwMlYZhYKEWZvusmEnB38dK7G4CeKFPvSVn7/R/5oMBMIzBZbaloxL+nOccn2MM+w4whsgH5WeodFJyTiE9ZeITqF2lW1tSMq3ZOy3AApscIstxq07ovpABMEwpa7i0cxr2/Q65gQ0AAPxxsU5cGLbLCIGi2NXoOUI7lHmDzQ0GvOT4HIM9NSd2JlCd9OnsudZJ8UKf4gRI5taFEABARDbX4323n3HOYbH/rm0OkdlgWMKvXgGCxEde7ByA3XSGSjKpvpJVZdhjBebl4fzzBwCAkTCpgnArShXvYwilAg/fmHdhP83JSVCX8Kk7aKuzJBYjuG2J/m4QOxOoZT0KTs4hkjc6kdUPqcaL3GsHRz+gFg8BrGzGEEakzoshyU3Gi53Ts/9fzmepKKgvRptB9nLyKazgsrROyRsDQCObok+j69C83BVq2Rz0WOrFuLdBkA6D0+4cO1Xg0bDP4yfYmF8FgGTuAUa1eCkWAGVXNo7Zdqmdc3A85LB4zCGSwGYMYRqy0Q8plyWXRj8A3hGfKKcKp2eX742f0+elhwUT5wagOmS8uGiHz78EQrHlmOqOtL5C3pVCcdoKpRvC2QpU4jRlHkNsYJ8f6T8/OR/CzXrrfjksh2ezPGRbNS6CEVvmaIeZlyXUuTF6wXT+KN18J+yfZc6R4+KQazw4ebuDOTiI32AODvJzQc0hfoOaQ/wGNYf4DWoO8RsrzZEZROyU/JEUaV7+lX7kBfnL4Wzniufpbk9LapKaXwdwEtz+FQTZgou+NRD9cgV3CxEA2Cnb+lBsJUK/yp5IyF8QYk6YT50TUTfhdONkcGe9Gubhd0+QvzuO6xA261G7/+4J8nfHaR1C6rx4/d0UBPHARiyT9K31DACja+61oW2nraGlGf91dqlGfjXMmuPFBYQj8Hz2kA/+2R3TBS1UHftW5DCY+lbxP09Q/nAGIA9XXzvWP1+MILtDaI4XJtVksqLOvsUiGbRqyMEh+tbRGzTOQyB9U95v5h0at43xbe995PfC9HtfmSIY0pyIvEMbf05NGz7qry8ivxN7rvFLza+DfLa0zqe7vV9ya0TEfzCuBPGbPTUXqMTpao+huoN89thbfSG/CZiDgxwfzMFBfi6oOcRvUHOI36DmEL9BzSF+g5pD/AY1h/gNag7xG9Qc4jeoOcRvUHOI36DmEL9BzSF+g5pD/AY1h/gNag7xG9Qc4jeoOcRvUHOI36DmEL9BzSF+g5pD/AY1h/gNag7xG9Qc4jeoOcRvUHOI36DmEL9BzSF+g5pD/AY1h/gNag7xG9Qc4jeoOcRvUHOI36DmEL9BzSF+g5pD/Ibcqx9Bjg/aOcRvUHOI36DmEL9BzSF+8397fN6eX4cd0wAAAABJRU5ErkJggg==) | ![image-20250112181026472](data:image/png;base64,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) | ![image-20250112174050053](data:image/png;base64,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) |

### 5、准备项目开发所需的图片素材

TIP

把项目的 psd 设计稿标注好切图，然后上传到蓝湖 （在公司，一般都有设计师来完成）

项目 psd 设计稿已上传到钉钉群文件，自行下载。关于如何用 ps 标注切图，讲面讲过了。

> 如果不会，可以然钉钉群看如下视频

![image-20250112185346892](https://www.arryblog.com/assets/img/image-20250112185346892.713436a8.png)

打开蓝湖，找到项目设计稿，导出项目的所有切图（正常情况下，设计师会把标注好的图片取上合理的名字，但如果没有，你就需要对图重命名）

![image-20250112185907916](https://www.arryblog.com/assets/img/image-20250112185907916.cfb943a2.png)

> 将导出来的图片素材，复制到项目的 `images` 文件夹下

### 6、实现响应式栅格系统

TIP

根据以下 3 步，来确定响应式栅格系统的具体代码

- 将页面分成 12 份，确定栅格布局不同份数所点比例
- 确定项目对应的断点，这里我们采用标准的断点

| 屏幕大小               | 栅格布局中 class 名区分 | 断点（阈值）              |
| :--------------------- | :---------------------: | :------------------------ |
| 超小屏（Extra small ） |                         | <576px                    |
| 小屏 （Small)          |           -sm           | 576px ~ 768px （含等于）  |
| 中屏 （Medium）        |           -md           | 768px ~ 992px （含等于）  |
| 大屏 (Large)           |           -lg           | 992px ~ 1200px（含等于）  |
| 超大屏 (X-Large)       |           -xl           | 1200px ~ 1400px（含等于） |
| 超大大屏（XX-Large)    |          -xxl           | >1400px                   |

- 确定适配方案，以 PC 端优先
- 按前面三步，实现响应式栅格系统（也就是书写 `media.css`样式）

```css
/* 
第一：我们将页面分成12分
第二：我们选择的断点是行业标准断点
第三：我们选择的适配方案，是PC端优先
*/

/* ....这里的css样式，会在屏幕宽大于1400px时生效.... */

.col-xxl-1 {
    width: 8.333333%;
  }
  .col-xxl-2 {
    width: 16.6666667%;
  }
  .col-xxl-3 {
    width: 25%;
  }
  
  .col-xxl-4 {
    width: 33.33333333%;
  }
  .col-xxl-5 {
    width: 41.66666667%;
  }
  .col-xxl-6 {
    width: 50%;
  }
  .col-xxl-7 {
    width: 58.33333333%;
  }
  .col-xxl-8 {
    width: 66.6666667%;
  }
  .col-xxl-9 {
    width: 75%;
  }
  .col-xxl-10 {
    width: 83.33333333%;
  }
  .col-xxl-11 {
    width: 91.66666667%;
  }
  .col-xxl-12 {
    width: 100%;
  }
  
  /* 当屏幕宽度大于1200px ，但小于等于1400px时，显示如下样式 */
  @media screen and (max-width: 1400px) {
    .col-xl-1 {
      width: 8.333333%;
    }
    .col-xl-2 {
      width: 16.6666667%;
    }
    .col-xl-3 {
      width: 25%;
    }
  
    .col-xl-4 {
      width: 33.33333333%;
    }
    .col-xl-5 {
      width: 41.66666667%;
    }
    .col-xl-6 {
      width: 50%;
    }
    .col-xl-7 {
      width: 58.33333333%;
    }
    .col-xl-8 {
      width: 66.6666667%;
    }
    .col-xl-9 {
      width: 75%;
    }
    .col-xl-10 {
      width: 83.33333333%;
    }
    .col-xl-11 {
      width: 91.66666667%;
    }
    .col-xl-12 {
      width: 100%;
    }
  }
  
  /* 当屏幕宽度大于992px ，但小于等于1200px时，显示如下样式 */
  @media screen and (max-width: 1200px) {
    .col-lg-1 {
      width: 8.333333%;
    }
    .col-lg-2 {
      width: 16.6666667%;
    }
    .col-lg-3 {
      width: 25%;
    }
  
    .col-lg-4 {
      width: 33.33333333%;
    }
    .col-lg-5 {
      width: 41.66666667%;
    }
    .col-lg-6 {
      width: 50%;
    }
    .col-lg-7 {
      width: 58.33333333%;
    }
    .col-lg-8 {
      width: 66.6666667%;
    }
    .col-lg-9 {
      width: 75%;
    }
    .col-lg-10 {
      width: 83.33333333%;
    }
    .col-lg-11 {
      width: 91.66666667%;
    }
    .col-lg-12 {
      width: 100%;
    }
  }
  
  /* 当屏幕宽度大于768px ，但小于等于992px时，显示如下样式 */
  @media screen and (max-width: 992px) {
    .col-md-1 {
      width: 8.333333%;
    }
    .col-md-2 {
      width: 16.6666667%;
    }
    .col-md-3 {
      width: 25%;
    }
  
    .col-md-4 {
      width: 33.33333333%;
    }
    .col-md-5 {
      width: 41.66666667%;
    }
    .col-md-6 {
      width: 50%;
    }
    .col-md-7 {
      width: 58.33333333%;
    }
    .col-md-8 {
      width: 66.6666667%;
    }
    .col-md-9 {
      width: 75%;
    }
    .col-md-10 {
      width: 83.33333333%;
    }
    .col-md-11 {
      width: 91.66666667%;
    }
    .col-md-12 {
      width: 100%;
    }
  }
  
  /* 当屏幕宽度大于576px ，但小于等于768px时，显示如下样式 */
  @media screen and (max-width: 768px) {
    .col-sm-1 {
      width: 8.333333%;
    }
    .col-sm-2 {
      width: 16.6666667%;
    }
    .col-sm-3 {
      width: 25%;
    }
  
    .col-sm-4 {
      width: 33.33333333%;
    }
    .col-sm-5 {
      width: 41.66666667%;
    }
    .col-sm-6 {
      width: 50%;
    }
    .col-sm-7 {
      width: 58.33333333%;
    }
    .col-sm-8 {
      width: 66.6666667%;
    }
    .col-sm-9 {
      width: 75%;
    }
    .col-sm-10 {
      width: 83.33333333%;
    }
    .col-sm-11 {
      width: 91.66666667%;
    }
    .col-sm-12 {
      width: 100%;
    }
  }
  
  /* 当屏幕宽度小于等于576px时，显示如下样式 */
  @media screen and (max-width: 576px) {
    .col-1 {
      width: 8.333333%;
    }
    .col-2 {
      width: 16.6666667%;
    }
    .col-3 {
      width: 25%;
    }
  
    .col-4 {
      width: 33.33333333%;
    }
    .col-5 {
      width: 41.66666667%;
    }
    .col-6 {
      width: 50%;
    }
    .col-7 {
      width: 58.33333333%;
    }
    .col-8 {
      width: 66.6666667%;
    }
    .col-9 {
      width: 75%;
    }
    .col-10 {
      width: 83.33333333%;
    }
    .col-11 {
      width: 91.66666667%;
    }
    .col-12 {
      width: 100%;
    }
  }
```



<details class="custom-block details" style="display: block; border-radius: 2px; margin: 1.6em 0px; padding: 1.6em; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Oxygen, Ubuntu, Cantarell, &quot;Fira Sans&quot;, &quot;Droid Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="outline: none; cursor: pointer; color: rgb(62, 175, 124);">点击查看完整源代码</summary><div class="language-css extra-class" style="position: relative; background-color: rgb(40, 44, 52); border-radius: 6px;"><pre class="language-css" style="color: rgb(204, 204, 204); background: transparent; font-family: Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace; font-size: 1em; text-align: left; white-space: pre; word-spacing: normal; word-break: normal; overflow-wrap: normal; line-height: 1.4; tab-size: 4; hyphens: none; padding: 1.25rem 1.5rem; margin: 0.85rem 0px; overflow: auto; border-radius: 6px; position: relative; z-index: 1;"><code style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(255, 255, 255); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token atrule" style="color: rgb(204, 153, 205);"><span class="token rule"></span><span class="token keyword" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token atrule" style="color: rgb(204, 153, 205);"><span class="token rule"></span><span class="token keyword" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token atrule" style="color: rgb(204, 153, 205);"><span class="token rule"></span><span class="token keyword" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token atrule" style="color: rgb(204, 153, 205);"><span class="token rule"></span><span class="token keyword" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token comment" style="color: rgb(153, 153, 153);"></span><span class="token atrule" style="color: rgb(204, 153, 205);"><span class="token rule"></span><span class="token keyword" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token selector" style="color: rgb(204, 153, 205);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token property" style="color: rgb(248, 197, 85);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span><span class="token punctuation" style="color: rgb(204, 204, 204);"></span></code></pre></div></details>

### 7、下载项目中用到的 iconfont 图标

TIP

进入网站 [iconfont 阿里图标库 (opens new window)](https://www.iconfont.cn/), 把下面图标加入到购物车，然后添加到项目，最后将所有图标下载下来。

![image-20250113111307270](https://www.arryblog.com/assets/img/image-20250113111307270.2e697060.png)

> 将存放图标对应文件夹名改为 `iconfont` ，放在当前项目根目录下。

温馨提示：

如果不会下载 iconfont 图标，可以进入 [iconfont 阿里矢量图标库 (opens new window)](https://www.arryblog.com/guide/css3/css-position.html#_4、何确定两个元素的的层叠顺序)页面，找到如下图所示位置， 查看详细操作教程

![image-20250113111609271](data:image/png;base64,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)

### 8、使用 Git 管理项目

TIP

按以下步骤，使用 Git 来管理项目

- 第一步：安装 Git
- 第二步：Git 的基础配置
- 第三步：初始化 Git 本地仓库
- 第四步：新建 `.gitignore` 文件 和 `README.md` 文件
- 第五步：使用 Gitee，新建远程仓库
- 第六步：添加远程仓库提交地址
- 第七步：Git 提交，提交代码到本地仓库 和 远程仓库

> 如果不会操作 Git，可以进入 [Git 初始化项目 (opens new window)](https://www.arryblog.com/guide/project/#七、git-初始化项目)查看详细 Git 操作教程。（需要视频版教程，可以联系客服免费获取）

## 三、正式进入项目开发

TIP

首先分析整个设计稿，确定接下来的布局方向。

整个项目由 9 大版组成，各版块之间相互独立，核心内容在 1200px 区域中居中显示。

> 所以，我们采取从上到下，一个版块一个版块来实现，最后再实现侧边栏相关内容布局（如：楼梯式导航、皮肤主题切换、右侧悬浮菜单）

![screencapture-arryblog-web-project-responsive-index-html-2025-01-13-14_22_04](https://www.arryblog.com/assets/img/screencapture-arryblog-web-project-responsive-index-html-2025-01-13-14_22_04.20e6b09a.png)

接下来，在 `index.html` 页面按顺序引入 css 文件

```html
<!DOCTYPE html>
<html lang="en" data-theme="turquoise">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>兼容多终端响应式网站</title>
    <!-- 重置 html 标签默认样式 -->
    <link rel="stylesheet" href="./css/reset.css" />
    <!-- 引入主题皮肤样式 -->
    <link rel="stylesheet" href="./css/skin-theme.css" />
    <!-- 引入全局样式 -->
    <link rel="stylesheet" href="./css/global.css" />
    <!-- 引入首页样式 -->
    <link rel="stylesheet" href="./css/index.css" />
    <!-- 引入媒体查询 栅格系统样式 -->
    <link rel="stylesheet" href="./css/media.css" />
  </head>
  <body></body>
</html>
```

## 四、网站头部导航

![GIF2025-1-1411-32-35](https://www.arryblog.com/assets/img/GIF2025-1-1411-32-35.2dcdedb8.gif)

> 以下是网站头部导航的具体实现步骤

### 1、第一步：渐变色背景的容器

![image-20250113150649967](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA+oAAAI7CAIAAAD06fa7AAAem0lEQVR4nO3dX7NkZ3me8ftZXl8xHyEHOU35JB8ogRhiO0aOY2yD/0BibBxbQoBA/xCSmJFGI2kkIYmjJwer194903uYXZWq9LOqfldX3bq4eovqw3derd1T//nBy+lOlbXWWmuttXb41n958HIAAAAAHIG1k6v/GcJaa6211lp7n3X7DgAAAByGJUknSbpv6+a6ruu6ruu6ro/qN7fvtf8Y55xzzjnnfKgvyeZ9KpxzzjnnnPOp7vadc84555zzw7hfXQUAAAAOw1qns/zNJkmndV3XdV3XdV2f1t2+AwAAAIdhu33fuD3dc84555xzzgd6fePBy5taa6211lprp+83Hr4y4FNYa6211lprX7z1jf3Z961wzjnnnHPOx3p948ErAQAAAHAEliRJW2uttdZaa+dvfXN/9r07VeGcc84555yP9e3hmU7KWmuttdZaO3xvb9+ttdZaa621w3dJpxNrrbXWWmvt/K1vPty+eWY70odzzjnnnHM+1uubD17pPVhrrbXWWmtH77PPvm9c/qyu67qu67qu69fu9U1/bRMAAABwEJaqSsVaa6211lp7gHX7DgAAAByFteqZB2o455xzzjnnQ31Jd3cn3Z3kzHVd13Vd13VdH9brvz78SQAAAAAcgXU7yldirbXWWmutnb5u3wEAAICjsCRJt7XWWmuttXb+1h89/Elf/T8BWGuttdZaa++xSye5+a1Wa6211lpr7eCtP7rr2fdO6rLquq7ruq7run7VvnTSe7rZdHRd13Vd13Vdn9bvvH2vmx/TdV3XdV3XdX1OX5J05+nti6Lruq7ruq7r+vX73c++AwAAABjIcu0PAAAAAOC+LJVKYq211lprrT3AengGAAAAOApLpersRM8555xzzjkf63/w7/7wPySp3MI555xzzjkf6t/64NV0UrHWWmuttdYO3/rWw59c+zNYa6211lpr77ffevjq6Ua+z27nOeecc8455/N8+973TmdvnHPOOeec86G+pJJUXayu67qu67qu6+P6tx6+mnRS1lprrbXW2uG7XJ7rrbXWWmuttUP39KurAAAAAMazVl37IwAAAAC4H2t3ktPTNBucc84555zzof7tD/aHZzqpcM4555xzzsd6fduz7wAAAMBBWFOVdKX6dKTnnHPOOeecT3W37wAAAMBRWKoqFWuttdZaa+0B9tsfvLrfxFtrrbXWWmtHb/23D3567f8CAAAAAOBerL198fs52+n+El3XdV3XdV3Xr9rXqrr7J+5E13Vd13Vd1/Xr9SVJtgt4a6211lpr7ez17DsAAABwGNy+W2uttdZae5itP/7gp70/DW+ttdZaa60dvR6eAQAAAI7CWtf+BAAAAADuydo3ut3Ic84555xzzqd6/bGHZwAAAICDsNxYn1XOOeecc875QF/2G/ntL1/lnHPOOeecz3UPzwAAAACH4XT7Xher67qu67qu6/q47vYdAAAAOAprVaWTirXWWmuttXb4un0HAAAADsN6epJmO9FvcM4555xzzkf6kqRvXjn7X7qu67qu67quD+v1Jx/+LL2f6K211lprrbWDd0mfTvTWWmuttdba4bukklRVkuKcc84555yP9j/54GcBAAAAcATWqmt/BAAAAAD3Y+2+9kcAAAAAcD+ec/veia7ruq7ruq7rw/q6/Q5r5WJ1Xdd1Xdd1XZ/W//TDn1++Za211lprrR249ae+eQYAAAA4CGvq+n+GsNZaa6211t5nl+Spv8bJWmuttdZaO3brv3/48wAAAAA4AmtvX/y+3cdvcM4555xzzke623cAAADgMCxJtgt4a6211lpr7fB1+w4AAAAchiVJzk70nHPOOeec87Hu9h0AAAA4DMu1PwAAAACA+7LWbp1wzjnnnHPOJ/vZwzNX/yycc84555zz3+v1Z559BwAAAA7CkqQTa6211lpr7fxdkqokVdtlPOecc84553ys1599+PNOKrHWWmuttdYO3/323VprrbXWWjt+/eoqAAAAcBiWqkrKWmuttdZae4B1+w4AAAAchbWqLp+K707VHU/L67qu67qu67p+xX66fa9U7+/vHl3XdV3XdV3XZ/XvPHpts9O7nHPOOeec86m+pNPduXlxzjnnnHPOp3p959Fr2c7yl6d7Xdd1Xdd1Xdcn9frOh/vDMwAAAABms971xTPWWmuttdbakXt2+75FzjnnnHPO+VCvlx69tunlm7qu67qu67quz+qXz75XpTuX6Lqu67qu67p+3V4vPfrFXad8a6211lpr7bitlz58bcQHsdZaa6211r5w3b5ba6211lp7lF2STsdaa6211lo7f+vPH/2iJ/w5wlprrbXWWvvCfWn75pnL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IL2f7q211lprrbWDd0l7eXl5eXl5eXl5eR3j5fbdWmuttdbaw2y9+vkHAQAAAHAE1qqr/xHCWmuttdZae791+w4AAAAchbXqZN3hnHPOOeecT/bT7XslfXqLc84555xzPtV/+sWHSe/RWmuttdZaO3frp59/MOKDWGuttdZaa1+4bt+ttdZaa609yi5Jp2OttdZaa62dv/WzLz7sCX+OsNZaa6211r5wf7p97/v2vzY455xzzjnnI93tu7XWWmuttYfZpdPp7uRidV3XdV3XdV2f1etnX3wYAAAAAEdgyeWx3lprrbXWWjty3b4DAAAAh2G59gcAAAAAcF+WSpJYa6211lpr5+/SSZLbB2o455xzzjnnU/3s9r2Kc84555xzPtr96ioAAABwFNZKJR1rrbXWWmvt+D3dvm9hg3POOeeccz7Uf/7Fo6T3aK211lprrZ279XPPvgMAAAAHYU1VOlXp/VjPOeecc845H+pu3wEAAICjsFaqczrRP7WJruu6ruu6ruuz+n77vv3PcM4555xzzsd6vfbbR+m91P4D50XXdV3XdV3X9Rn9ji+OrFTf8e/puq7ruq7run7lfnH7bq211lprrZ269doXj3IH2/u6ruu6ruu6rg/q9dpv7zy+AwAAABjHmr7x85M+55xzzjnnfJyfbt9rD6fdf1LXdV3XdV3X9UH9Oc++AwAAABjHWvXsyd5aa6211lo7c92+AwAAAIfB7bu11lprrbWH2SXpdJ7Zvii6ruu6ruu6rl+91y9++1EAAAAAHIE13cl+H7/BOeecc845H+mn2/cBn4RzzjnnnHP+At+efd+epWnOOeecc875ZK9fevYdAAAAOAhrp9NJVbpP9/Kcc84555zzke72HQAAADgMy411mnPOOeeccz7Z3b4DAAAAh2G7fe8k6dvT/e66ruu6ruu6rg/qbt8BAACAw7C8+EcAAAAAzGCt7Z/bl9Gcvo2mbi/qdV3XdV3XdV0f0z08AwAAAByGtfbvgr/d85O+ruu6ruu6rutjer3+24/u+hFrrbXWWmvtvH39y8cDPoW11lprrbX2xVuv78++b4VzzjnnnHM+1p93+749YaPruq7ruq7r+qB+e/t+xvZTl+i6ruu6ruu6fs1eb3z5eLPtQM8555xzzjkf6ze375Xbkz7nnHPOOed8otcbzzz7vnFedF3XdV3XdV2f0Zd0Oknvrz5zXdd1Xdd1Xdcn9dtn3wEAAAAMZ93O8ZWy1lprrbXWTl+37wAAAMBRWNMXbXtM/hJd13Vd13Vd16/a680vH3eyX8iHc84555xzPtff+K2HZwAAAIBjsFbtZ3prrbXWWmvt7F2S7o611lprrbV2/tabX34cAAAAAEdgPZ3iK9Zaa6211trpe3b73klxzjnnnHPOx3q9efPXNg36VJxzzjnnnPM7vN768uPNrbXWWmuttdP3zS8fX7TtsZrLn9V1Xdd1Xdd1/Zq93rrrm2e2n9R1Xdd1Xdd1fVRfOul0bvf0A7qu67qu67quT+t3374DAAAAGMiSZ0/31lprrbXW2qHr9h0AAAA4DMu1PwAAAACA+7Jsv8FaVUmqzlzXdV3XdV3X9WndwzMAAADAUVgqqdsTfZ25ruu6ruu6ruvD+nb7XknnBOecc84553yov/3VJ+m93W6nStd1Xdd1Xdf1Ub3e/vLjO9611lprrbXWDtyz2/fzkz7nnHPOOed8nNfbvnkGAAAAOAhrqrId6M93+4eu67qu67qu66O623cAAADgKKxVdXOiH/NID+ecc8455/wuf/vLT7JHa6211lpr7eStX331ybX/CwAAAACAe7F2J+lK9c2JnnPOOeeccz7T3b4DAAAAR2FNJ9mO8nvjnHPOOeecj/TT7fvT726X85f/lq7ruq7ruq7rV+2/+vKTy/c555xzzjnnA32pSmp/cc4555xzzif7r776JJ1UrLXWWmuttcO33vnq0/1Sfmucc84555zzoX7H7XtV+umi67qu67qu6/qEvt2+n79/frrXdV3XdV3XdX1Qr3du/tqmy3c555xzzjnnk/z82XcAAAAAo1mTPum1/yTBOeecc845//1ev/7q082ttdZaa621w3fpJGlrrbXWWmvt/K1fe/YdAAAAOAhLJ50k6XTOXNd1Xdd1Xdf1aX2/fa/9Hc4555xzzvlUX7J5nwrnnHPOOed8rHv2HQAAADgMy7U/AAAAAID7slRVEmuttdZaa+0B1sMzAAAAwFFYqqrOTvScc84555zzub7dvldOv83KOeecc845n+vvfv3kpJ1UOOecc84552O93v3q082ttdZaa6210/fdr58M+BTWWmuttdbaF2+9e/rmmcv3o+u6ruu6ruv6qF7vff2k73rTWmuttdZaO26fvn0P55xzzjnnfKy7fbfWWmuttfY4++5X+xdHnuL2zu66ruu6ruu6ro/p9d7N974DAAAAmM2aPruKv92ulK7ruq7ruq7rs7rbdwAAAOAoLEnSsdZaa6211s7fpeLl5eXl5eXl5eXldZDXe9s3z1w8XHNC13Vd13Vd1/Uxfal6zrle13Vd13Vd1/Vp/b2vnzx1rt/oi/O+ruu6ruu6ruvX7vX+158FAAAAwBFYO51OVfrpPZ3udV3XdV3XdV2f092+AwAAAEdhTTrJ/nBNOOecc84552P9dPt+/Q/COeecc845f6G///WTOR+Gc84555xz/nu8fvP1Z70Ha6211lpr7eg9+9XVLXLOOeecc86Hev1mO75X0vtbnHPOOeec85F+/qurnRTnnHPOOed8rrt955xzzjnn/Ci+H98BAAAAjGdJVZLzrYui67qu67qu6/qE7vYdAAAAOAzLfpSvi9V1Xdd1Xdd1fVh3+w4AAAAchXU7yydJJ7umO7qu67qu67quD+tu3wEAAIDD8Lzbd84555xzzvk4rwen2/dKen+Tc84555xzPtHrwe8+DwAAAIAjsKb7Ip6f9HVd13Vd13Vdn9JPt+8vvqbnnHPOOeecX90ffP150qlKd1L7+336MV3XdV3XdV3Xx/R66Nl3AAAA4CCs3Td+ebrXdV3XdV3XdX1Qd/sOAAAAHIYlSTrZDvScc84555zzwV4Pf/dF0tuNvLXWWmuttXbyLkmnY6211lprrZ2/N8++byf6cM4555xzzsf6sqe+fZdzzjnnnHM+0uuD331xW1Occ84555zzsX72xZGDPhXnnHPOOef8Dj+/fT/n/Gd1Xdd1Xdd1XR/R16Q3PdvqpHRd13Vd13Vdn9afc/sOAAAAYBxr0pttp3vOOeecc875WP+/dZ8K38wkNHYAAAAASUVORK5CYII=)

- 因为导航和轮播图在同一个容器，所以在实现菜单前，先要创建好渐变色背景的容器
- 背景色是一个从上到下的径向渐变，并且颜色有 40% 的透明度。
- 因为我们这里的颜色是直接通过 CSS var 函数引用 主题皮肤中的自定义属性来实现的，所以只能通过以下方式实现背景色透明度

```css
background-image: linear-gradient(
  to bottom,
  var(--primary--color),
  var(--white-color)
);
pacity: 0.4;
```

- 这里我们采用伪元素来绘制这个渐变的背景，然后定位在当前容器上面。
- 为了让菜单还有轮播图内容能显示在渐变背景上面，所以我们还要创建一个用来放 菜单和轮播图的 div 元素，然后采用定位，定位在渐变的背景色上面。

```html
<style>
  .header {
    width: 100%;
    height: 758px;
    position: relative; /* 相对定位 */
  }
  .header::before,
  .header .header-content {
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
  }
  .header::before {
    content: "";
    background-image: linear-gradient(
      to bottom,
      var(--primary--color),
      var(--white-color)
    );
    opacity: 0.4;
  }
  /* .header .header-content {
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    } */
</style>

<!-- 网页头部 开始 -->
<header class="header">
  <div class="header-content">绝对定位元素 - 有来放置导航和轮播图</div>
</header>
<!-- 网页头部 结束 -->
```

### 2、第二步：制作顶部放置 logo 和 导航容器

![image-20250113152535953](data:image/png;base64,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AMBI+gjXpFoP7rXy5A0arfW+DQAAAAAYSR3hmlTrwb0k6YuXtNb7NgAAAABgJke4JtV6ci/n/1yx3TvVWu/cAQAAAACM5AjXpFpP7uV825SZj2MAAAAAwEyOcE3KPNRLXZxiqzu22+177AAAAACAmRzt+tRuH7TXn7z1XAAchn/1a7+591sAAAAAAOzAZ92iAXZlrap0UmHmQxgAAAAAMJJK7X9NyjzYzpMCAAAAAAAAmM75POnGdvdUa6211lprrbXWWmutJ/WSTqeT0z/79GLb7Xa73W632+12u91ut9vtdvuQvT774Pn0+e4pMzMzMzMzMzMz8zwv6dM9U2ZmZmZmZmZmZuaZXqqSVCpJaa211lprrbXWWmut9cCuz771fAAAAAAAAABgMGvV3m8BAAAAAAAAAHZl7d77LQAAAAAAAADArqxVSSf3niq12+12u91ut9vtdrvdbrfb7fYBe33uree3p8zMzMzMzMzMzMwzXZ978MLe74GZmZmZmZmZmZl5T9fn/N49AAAAAAAAgNmsqUPcr2VmZmZmZmZmZmbey0vS6TAzMzMzMzMzMzOPdf3pgxcCAAAAAAAAAINZ+3THNMn5kKnWWmuttdZaa6211lpPaudJAQAAAAAAAExnSdLdzMzMzMzMzMzMzGPtPCkAAAAAAACA6dyeJ83F3VOttdZaa6211lprrbWe086TAgAAAAAAAJjOsvcbAAAAAAAAAICdWSvppM7PtdZaa6211lprrbXWelrXnz544RBvRGuttdZaa6211lprrXfq+jPfTwoAAAAAAABgNkuSTpiZmZmZmZmZmZnHeklVJUlVorXWWmuttdZaa6211hP7zx680EklzMzMzMzMzMzMzDO9JBf3TZmZmZmZmZmZmZkH2u84AQAAAAAAABjOUlVJMTMzMzMzMzMzM4+186QAAAAAAAAAprNWVXeq7vnyUrvdbrfb7Xa73W632+12u91un7A/86nf/e2kt5umlerzH9bpz+12u91ut9vtdrvdbrfb7Xa7/cr3+vOHL55e2tBaa6211lprrbXWWuthvaTPj26ttdZaa6211lprrbUe2BfnSS99eT/Vbrfb7Xa73W632+12u91ut9uveq8/f/BiAAAAAAAAAGAwa9U9t1OZmZmZmZmZmZmZ53g7T7r1htZaa6211lprrbXWWs/q+vzDF7dnl778K7vdbrfb7Xa73W632+12u91uv+79mU99+rfTuUttf2K32+12u91ut9vtdrvdbrfb7de+1+cfvpR0nr6jyszMzMzMzMzMzDzF9fkH93zunpmZmZmZmZmZmXmOnSdlZmZmZmZmZmbm6V6SToeZmZmZmZmZmZl5rOsvHr7Uu9+tZWZmZmZmZmZmZt7P9fmHL6Zz4u6f2O12u91ut9vtdrvdbrfb7Xb7te/OkzIzMzMzMzMzM/N01+cfvpTu1PnGqdZaa6211lprrbXWWg/r+ouHLwUAAAAAAAAABrMk6W5mZmZmZmZmZmbmsXaeFAAAAAAAAMB0liRJf8yrdrvdbrfb7Xa73W632+12u91+/ftSSVLb15Xesd1ut9vtdrvdbrfb7Xa73W63X/++fe6+z69Ga6211lprrbXWWmutp/Xd86Raa6211lprrbXWWms9q/2OEwAAAAAAAIDprFWV3s6XdrTWWmuttdZaa6211npe1xcevtTnm6aVaK211lprrbXWWmut9bReUlVJpSrRWmuttdZaa6211lrrif0F308KAAAAAAAAYDZrVR3g4/9aa6211lprrbXWWmu9WztPCgAAAAAAAGA6y/YxfGZmZmZmZmZmZuaxri88fDnp823T0lprrbXWWmuttdZa62ldX3z75XRS50VrrbXWWmuttdZaa62HdX3x4cudPr9SOXel7Ha73W632+12u91ut9vtdrt9wu48qdZaa6211lprrbXWenrXF0/fT7r3G9Faa6211lprrbXWWuudur749ssBAAAAAAAAgMGs6Rzhfq3WWmuttdZaa6211lrv1fWXb7/c57kSrbXWWmuttdZaa621ntbn33Ha/Y1orbXWWmuttdZaa631Tl1/+faPkz7PzMzMzMzMzMzMzOP85HnSS7Y/sNvtdrvdbrfb7Xa73W632+32a9+dJ2VmZmZmZmZmZubpXpLuTtLpaK211lprrbXWWmut9cDezpMCAAAAAAAAwFzW0x3TQxxuZWZmZmZmZmZmZt7B9Vdv//h8o/QJKrHb7Xa73W632+12u91ut9vt9gn7M//x07/zxJ/ddtntdrvdbrfb7Xa73W632+12+4S9/sr3kwIAAAAAAACYzdpJulPbndQ6dZKU3W632+12u91ut9vtdrvdbrdP2J0nBQAAAAAAADCdJUmnk3Ry07lou91ut9vtdrvdbrfb7Xa73W6/7t15UgAAAAAAAADTWZLc3ku9dex2u91ut9vtdrvdbrfb7Xa7fcjuPCkAAAAAAACA6Sx7vwEAAAAAAAAA2JmlqpJUpZKqqou22+12u91ut9vtdrvdbrfb7fYRu8/dAwAAAAAAABjOWlXpTirpaK211lprrbXWWmut9byuL7394/MzZmZmZmZmZmZm5omuL73zk0O8EWZmZmZmZmZmZuadfHuedENrrbXWWmuttdZaa62n9ZKbH3ZKaa211lprrbXWWmut9cT+kt+7BwAAAAAAADCbtaqOcK5Va6211lprrbXWWmut9+r60ts/STr3UHa73W632+12u91ut9vtdrvdPmGvL9/83v2G1lprrbXWWmuttdZaD+slfX50X3Tsdrvdbrfb7Xa73W632+12u33IXl9+5ycBAAAAAAAAgMEst3dSmZmZmZmZmZmZmUfaeVIAAAAAAAAA01mSpM//lzu22+12u91ut9vtdrvdbrfb7fZr35dKpVKV1M3jou12u91ut9vtdrvdbrfb7Xa7/dr3+vI7PzndPU1S0VprrbXWWmuttdZa62ldf/3OT++8eGm73W632+12u91ut9vtdrvdbr/yfUm6O0m6c+5L2+12u91ut9vtdrvdbrfb7Xb7le8350kr92C32+12u91ut9vtdrvdbrfb7de/35wn7e6+Y7vdbrfb7Xa73W632+12u91uv/797nlSrbXWWmuttdZaa621ntX119vv3d+8dIndbrfb7Xa73W632+12u91utw/Y6yvv/HR7yszMzMzMzMzMzDzTd86Taq211lprrbXWWmut9bC+PU96F7vdbrfb7Xa73W632+12u91un7Av29JJp/Ok7Xa73W632+12u91ut9vtdrt9wl5fefTT0/gUFbvdbrfb7Xa73W632+12u91un7Av6dy9k9o3D7vdbrfb7Xa73W632+12u91uv/a9vvLOTwMAAAAAAAAAg1n2fgMAAAAAAAAAsDNLVSWpShKttdZaa6211lprrbUe2D53DwAAAAAAAGA6958nrY+5t2q32+12u91ut9vtdrvdbrfb7de3P/OfPv07uY+6d7Xb7Xa73W632+12u91ut9vt9qvb66uPXkn36cZporXWWmuttdZaa6211tO6vvrOTzuphJmZmZmZmZmZmXmml5w/iP+ky2632+12u91ut9vtdrvdbrfbp+xf9Xv3AAAAAAAAAGazVlWfn9SdE6d2u91ut9vtdrvdbrfb7Xa73X71u/OkAAAAAAAAAKZzOk96904qMzMzMzMzMzMz8xDXV995Ze/3wMzMzMzMzMzMzLyn628evbL3mVYAAAAAAAAA2JM1nT7fN62U1lprrbXWWmuttdZaT2vnSQEAAAAAAABMZ0mSDjMzMzMzMzMzM/NY19cevdqnIXV+Kcn53Kndbrfb7Xa73W632+12u91ut1/5Xn/z6JXLF9NP2m632+12u91ut9vtdrvdbrfbr31fKpVKVVI3j4u22+12u91ut9vtdrvdbrfb7fZr38/nSevJO6kbdrvdbrfb7Xa73W632+12u90+YK+vPXr1vhe11lprrbXWWmuttdZ6Sn/MeVJmZmZmZmZmZmbmMb48T8rMzMzMzMzMzMw80fW1R68EAAAAAAAAAAazJrX3ewAAAAAAAACAPVmTPh0vvYvdbrfb7Xa73W632+12u91utw/Y6+uPXt2eMjMzMzMzMzMzM8/00knSzMzMzMzMzMzMzGNdX3/31XRObLdPtdZaa6211lprrbXWelLX1x69mvR5ZmZmZmZmZmZmZh7n+vqjVwMAAAAAAAAAg1mS9MVzrbXWWmuttdZaa621ntZLKpWkkkRrrbXWWmuttdZaa60nts/dAwAAAAAAABjOUlXJ6b5pPWG73W632+12u91ut9vtdrvdbh+xO08KAAAAAAAAYDprVaU7VUknWmuttdZaa6211lprPa6dJwUAAAAAAAAwnaWqKmFmZmZmZmZmZmae67999GondTppevKG3W632+12u91ut9vtdrvdbrdP2Otv3/1ZAAAAAAAAAGAwa7r3fg8AAAAAAAAAsCdrVd3cKN1OmWqttdZaa6211lprrfWoXjpJdzrp1lprrbXWWmuttdZa64Fdf+f7SQEAAAAAAADMZt1unJ7PmTIzMzMzMzMzMzOPs/OkAAAAAAAAAKazJOkOMzMzMzMzMzMz81g7TwoAAAAAAABgOkuSdJiZmZmZmZmZmZnH2nlSAAAAAAAAANO5OE+6obXWWmuttdZaa6211sN6qWyPJKncPrPb7Xa73W632+12u91ut9vt9iF7/d27P0vnNDyF3W632+12u91ut9vtdrvdbrcP2Ovv333tEG/Ebrfb7Xa73W632+12u91ut9t32uvv3/1Zn59WorXWWmuttdZaa6211tN6O08KAAAAAAAAAHNZkyR9flpaa6211lprrbXWWms9resb773Wfe8rsdvtdrvdbrfb7Xa73W632+32CfvN7zjdpex2u91ut9vtdrvdbrfb7Xa7fcJe33j3tT5vzMzMzMzMzMzMzAN9c570qX3Dbrfb7Xa73W632+12u91ut9uvf69vvPfaPX/GzMzMzMzMzMzMPMbb5+634fIe6vYHdrvdbrfb7Xa73W632+12u91+/fv5POnp2fnPbmy32+12u91ut9vtdrvdbrfb7de+1zfefS0AAAAAAAAAMJglVUmedt1Z7Ha73W632+12u91ut9vtdrv9SnfnSQEAAAAAAABMZ6nTHdMk2bou2m632+12u91ut9vtdrvdbrfbr353nhQAAAAAAADAdNaqOv+804bWWmuttdZaa6211lrPaudJAQAAAAAAAExnPX0OHwAAAAAAAACmsqbT6fO90kr6/FLZ7Xa73W632+12u91ut9vtdvuEvf7nez8PAAAAAAAAAAxmTff/+a8AAAAAAAAA4HpZq+r2pOnlqVOttdZaa6211lprrbWe0UsnpyOl3VprrbXWWmuttdZaaz2w65u+nxQAAAAAAADAbNbzfdNKOlXn3ga73W632+12u91ut9vtdrvdbr/+3XlSAAAAAAAAANNZst02TdLRWmuttdZaa6211lrrgV3ffO/1UyanU6ZP2G632+12u91ut9vtdrvdbrfbr3xfkj497Zz70na73W632+12u91ut9vtdrvdfuX7vedJtdZaa6211lprrbXWelD7HScAAAAAAAAA01nrdN+0zovWWmuttdZaa6211lrP6vrmez9/4qVL7Ha73W632+12u91ut9vtdrt9wF7fOn0/6d5vxG632+12u91ut9vtdrvdbrfbd9qX7VnSnX7Sdrvdbrfb7Xa73W632+12u90+Yq9vPX59G5KkorXWWmuttdZaa6211tO6vvXezzup86K11lprrbXWWmuttdbTevt+UgAAAAAAAACYy5IkaWZmZmZmZmZmZuaxrm8/fr07VUknFa211lprrbXWWmuttZ7W2+fuOylmZmZmZmZmZmbmma5vb793f4g3w8zMzMzMzMzMzLyDl3Q6YWZmZmZmZmZmZh7r+vbjX6Q7lSRJaa211lprrbXWWmut9bSub7/3eieV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)

```html
<style>
  .top {
    height: 80px;
  }
  /* 这个样式为通用样式，移到 global.css 中，但是这里为了演示，暂时放在这里。 */
  .layout {
    max-width: 1200px; /* 这里要用 max-width ，这样页面缩小时，容器也会缩小 */
    margin: 0 auto;
  }
  .top .top-content {
    height: inherit;
    background-color: red; /* 后面会去掉 */
  }
</style>

<!-- 网页头部 开始 -->
<header class="header">
  <div class="header-content">
    <!-- top开始 -->
    <div class="top">
      <div class="top-content layout"></div>
    </div>
    <!-- top结束 -->
  </div>
</header>
<!-- 网页头部 结束 -->
```

### 3、第三步：添加 logo 和 导航

TIP

利用 flex 弹性布局实现 logo 和导航水平两端对齐，同时垂直居中对齐

![image-20250113153716621](https://www.arryblog.com/assets/img/image-20250113153716621.39fe7bfa.png)

```html
<style>
  .top .top-content {
    /* 省略了部分css 具体见前面 */
    display: flex; /* 开启弹性布局 - 所有子项默认水平排列 */
    align-items: center; /* 垂直方向居中对齐 */
    justify-content: space-between; /* 水平方向两端对齐 */
  }
  .top ul.menu {
    display: flex; /* 开启弹性布局 - 所有子项默认水平排列 */
  }
</style>

<!-- top开始 -->
<div class="top">
  <div class="top-content layout">
    <!-- logo开始 -->
    <div class="logo">
      <a href="#">
        <img src="./images/logo.png" alt="艾编程logo" width="118" />
      </a>
    </div>
    <!-- logo开始 -->
    <!-- 导航开始 -->
    <nav>
      <ul class="menu">
        <li><a href="">网站首页</a></li>
        <li><a href="">国内游</a></li>
        <li><a href="">出镜游</a></li>
        <li><a href="">周边游</a></li>
        <li><a href="">主题游</a></li>
        <li><a href="">自由行</a></li>
        <li><a href="">合作案例</a></li>
        <li><a href="">关于我们</a></li>
      </ul>
    </nav>
    <!-- 导航结束 -->
  </div>
</div>
<!-- top结束 -->
```

### 4、第四步：美化导航

![image-20250113155227841](https://www.arryblog.com/assets/img/image-20250113155227841.e1ce75f7.png)

- 为了让鼠标移入导航文字上下区域和左右间隙也能有移入效果，我们需要给 a 标签添加行高 80px 。
- 行高 80px 也能让文字在垂直方向上距中对齐

```css
.top .top-content {
  /* 省略了部分css 具体见前面 */
  /* 去掉 红色的背景 */
  /* background-color: red;  后面会去掉  */
}

.top ul.menu li a {
  display: block; /* 块级元素 */
  line-height: 80px; /* 行高等于父元素的高度 文字垂直居中显示 */
  padding-right: 16px; /* 右内边距 */
  padding-left: 15px; /* 左内边距 */
  color: var(--font-black-color);
  font-size: 18px;
}
/* 鼠标移入改变文字颜色 */
.top ul.menu li a:hover {
  color: var(--primary--color);
}
```

### 5、第五步：鼠标移入导航时，显示动态下划线

![GIF2025-1-1316-13-03](https://www.arryblog.com/assets/img/GIF2025-1-1316-13-03.f4476986.gif)

- 给`a` 标签 或 `li` 标签添加 `::after` 伪元素,来实现动态下划线
- 当定位元素的`left` 和 `right` 属性值都为 `50%` 时，相当于隐藏元素

```css
ul.menu li {
  position: relative; /* 开启定位，为伪元素定位做准备 */
}

/* 给 a 标签 或 li标签添加 ::after 伪元素,来实现动态下划线 */
ul.menu li::after {
  content: "";
  position: absolute;
  /* 当定位元素的 left 和 right 属性值都为 50%时，相当于隐藏元素 */
  left: 50%;
  right: 50%;
  bottom: 0;
  height: 2px;
  background-color: var(--primary--color);
  transition: left 0.3s, right 0.3s; /* 为属性添加过渡动效果 */
}

/* 鼠标移入改变伪元素的宽 */
ul.menu li:hover::after {
  left: 0;
  right: 0;
}
```

### 6、第六步：实现二级下拉菜单

![GIF2025-1-1316-38-34](https://www.arryblog.com/assets/img/GIF2025-1-1316-38-34.8fb261a6.gif)

二级菜单中的 a 标签会继承 一级菜单中的`padding: 0 16px 0px 15px;` 所以在这一步中，要重置 a 标签的 padding 值。

```html
<style>
  ul.menu li .menu-dropdown {
    position: absolute;
    left: 0;
    right: 0;
    top: 80px;
    background-color: var(--white-color);
    transform-origin: top center; /* 设置变换的原点 顶部的中间 */
    transform: scaleY(0); /* 初始状态为折叠  缩放到0 元素完全看不见 */
    transition: transform 0.3s; /* 为属性添加过渡动效果 */
  }

  ul.menu li .menu-dropdown {
    padding-top: 2px;
    padding-bottom: 8px;
  }

  ul.menu li .menu-dropdown dd {
    overflow: hidden;
  }
  .top ul.menu li .menu-dropdown dd a {
    /* display: block; */
    line-height: 39px;
    padding: 0px; /* 重置 a 标签 继承的 样式*/
    text-align: center;
  }
  .top ul.menu li:hover .menu-dropdown {
    transform: scaleY(1); /* 初始状态为折叠  缩放到0 元素完全看不见 */
  }
</style>

<!-- 导航开始 -->
<nav>
  <ul class="menu">
    <li><a href="">网站首页</a></li>
    <li>
      <a href="">国内游</a>
      <dl class="menu-dropdown">
        <dd><a href="#">北京</a></dd>
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">广东</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">云南</a></dd>
      </dl>
    </li>
    <li>
      <a href="">出镜游</a>
      <dl class="menu-dropdown">
        <dd><a href="#">泰国</a></dd>
        <dd><a href="#">日本</a></dd>
        <dd><a href="#">美国</a></dd>
        <dd><a href="#">台湾</a></dd>
        <dd><a href="#">海岛</a></dd>
      </dl>
    </li>
    <li>
      <a href="">周边游</a>
      <dl class="menu-dropdown">
        <dd><a href="#">北海</a></dd>
        <dd><a href="#">桂林</a></dd>
        <dd><a href="#">张家界</a></dd>
        <dd><a href="#">凤凰</a></dd>
      </dl>
    </li>
    <li>
      <a href="">主题游</a>
      <dl class="menu-dropdown">
        <dd><a href="#">游学</a></dd>
        <dd><a href="#">自组</a></dd>
      </dl>
    </li>
    <li>
      <a href="">自由行</a>
      <dl class="menu-dropdown">
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">丽江</a></dd>
      </dl>
    </li>
    <li><a href="">合作案例</a></li>
    <li><a href="">关于我们</a></li>
  </ul>
</nav>
<!-- 导航结束 -->
```

### 7、鼠标移入二级菜单右移动画

![GIF2025-1-1317-03-04](https://www.arryblog.com/assets/img/GIF2025-1-1317-03-04.3ab7948f.gif)

- 利用 a 标签的伪类 `::before` 来制作 菜单前面的小竖线，一开始使用 `display:none` 隐藏小竖线
- 当鼠标移入到 dd 元素上时，让 a 的伪类 `::before` 显示，同时，a 标签向右移动 10px
- 给 a 标签加上 过渡动画，这样 a 标签向右移动时就有过渡动画效果

```css
ul.menu li .menu-dropdown dd a {
  /* 省略了部分css 具体见前面 */
  position: relative; /* 开启定位，为伪元素定位做准备 */
  transition: transform 0.5s; /* 为属性添加过渡动效果 */
}

/* 制作竖线 */
.menu-dropdown dd a::before {
  content: "";
  position: absolute;
  top: 7px;
  bottom: 7px;
  left: 10px;
  width: 2px;
  background-color: var(--primary--color);
  display: none; /* 初始状态隐藏 */
}

/* 鼠标移入 a标签向右移动 10px */
.menu-dropdown dd:hover a {
  transform: translateX(10px);
}
/* 鼠标移入显示竖线 */
.menu-dropdown dd:hover a::before {
  display: block;
}
```

### 8、实现吸顶盒导航效果

![GIF2025-1-1317-44-37](https://www.arryblog.com/assets/img/GIF2025-1-1317-44-37.c831e6d7.gif)

**分析吸顶盒导航效果**

- 刚开始进到页面，导航就显示在他原来的位置（浏览器的顶部）。
- 当浏览器的滚动条的滚动距离 > 1 时
  - 元素先移出屏幕，然后再从屏幕是上方淡入移下来，最后固定在浏览器顶部
  - 导航最外层容器背景变为白色，同时添加向下的阴影

**吸顶盒导航实现原理**

- 我们可以定义一个 `sticky` class 类，来实现导航移入动画。

```css
.sticky {
  width: 100%; /* 这个宽度一定要加 ，元素定位后，为行内块元素特性 */
  position: fixed;
  top: 0;
  box-shadow: 0 2px 5px #ddd; /* 添加阴影 */
  background-color: var(--white-color); /* 背景颜色 */
  animation: sticky-animation ease-out 0.5s both; /* 动画效果 */
}
/* 定义帧动画 */
@keyframes sticky-animation {
  0% {
    opacity: 0; /* 初始状态透明度为0 */
    transform: translateY(-100%); /* 初始状态向上移动自身距离 */
  }

  100% {
    opacity: 1; /* 结束状态透明度为1 */
    transform: translateY(0); /* 结束状态向上移动0 */
  }
}
```

- 当浏览器滚动条滚动距离 > 1 时，给`class='top'` 的元素添加 `sticky` class ，实现盒子从上慢慢移下的效，否则，将 `sticky` class 从元素身上移除

```html
<!-- top开始 -->
<!--
给 class="top" 元素添加 `id="J_top"` 方便我们通过 JS获取到该元素.
同时我们只要看到页面中元素的 id名是以大写字母 J_ 开头的，就知道当前元素有JS操作他。
-->
<div class="top" id="J_top">
  <!--- 省略部分 html 结构 -->
</div>
<!-- top开始 -->
/* 实现吸顶盒导航 */
function stickyMenu() {
  // 获取 top元素
  const _top = document.getElementById("J_top");
  // 监听浏览器的滚动事件
  window.addEventListener("scroll", function () {
    // 获取当前滚动条滚动的距离
    let scrollTop =
      document.documentElement.scrollTop || document.body.scrollTop;
    if (scrollTop > 1) {
      // 就给 top 元素添加 sticky 类名
      _top.classList.add("sticky");
    } else {
      _top.classList.remove("sticky");
    }
  });
}
stickyMenu(); // 调用函数
```

### 9、实现导航响应式效果

![GIF2025-1-1318-18-36](https://www.arryblog.com/assets/img/GIF2025-1-1318-18-36.1bff28c7.gif)

当页面宽度 <=992px 时，导航隐藏，在最右侧显示 ![image-20250113175039595](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAdCAIAAABE/PnQAAABOUlEQVRIibWWwU3DQBBF39+sEEfSVUgHFJBOSAcgIaUAKoBUENogZ8LR989hvbGTWFx2PIev0bc1X+uZP159dN8ABl1iiWY+YTAuzxjlQXxGgDQSjc3zhegMmBFCnvioDuEz7j/XrX4In6UyAafDZr19P9EWy6e3l91qOWKyXQUX943VgbuFXSuW0Gd3bK/7T6SiZ5uqHZv3PeixHCo0z9gg4zpcfV7eaeczveZIedgsAXyq8+objOGLk7F+vzbr5wgfvO5WD5LAkiAxtDwkbIMH1L47MrXSo/J0NrLBHnZKFJ/LKlJt/BW282liHEIxjU8wB6ahI1cYxGeKrfVzCPPB41IWsiyU+j9akAsAzhWNsfbdsS6mWTBdKM6Q534XauRBjY7bzGfb9YYxeRdp5eutoihP+LOV/wPi+OgEPRkiEAAAAABJRU5ErkJggg==) 图标

- 通过媒体查询，在检测 **页面视口宽 <=992px** 时，将导航隐藏 （以下代码要放在所有 css 之后）

```css
/* 以下 css  要写在所有页面样式之后 */
@media screen and (max-width: 992px) {
  /* 最后是隐藏整个 nav 标签，而不只是 ul
    .top ul.menu {
    display: none 
}
    */

  .top nav {
    display: none; /* 隐藏导航 */
  }
}
```

- 在 `class='logo'` 元素的后面，添加 ![image-20250113175039595](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAdCAIAAABE/PnQAAABOUlEQVRIibWWwU3DQBBF39+sEEfSVUgHFJBOSAcgIaUAKoBUENogZ8LR989hvbGTWFx2PIev0bc1X+uZP159dN8ABl1iiWY+YTAuzxjlQXxGgDQSjc3zhegMmBFCnvioDuEz7j/XrX4In6UyAafDZr19P9EWy6e3l91qOWKyXQUX943VgbuFXSuW0Gd3bK/7T6SiZ5uqHZv3PeixHCo0z9gg4zpcfV7eaeczveZIedgsAXyq8+objOGLk7F+vzbr5wgfvO5WD5LAkiAxtDwkbIMH1L47MrXSo/J0NrLBHnZKFJ/LKlJt/BW282liHEIxjU8wB6ahI1cYxGeKrfVzCPPB41IWsiyU+j9akAsAzhWNsfbdsS6mWTBdKM6Q534XauRBjY7bzGfb9YYxeRdp5eutoihP+LOV/wPi+OgEPRkiEAAAAABJRU5ErkJggg==) 图标
- 图标采用 `iconfont` 图标

```html
<!-- 引入字体图标样式 -->
<link rel="stylesheet" href="./iconfont/iconfont.css" />
<!-- 引入全局样式 -->

<style>
  /* 控制栏目图标样式 */
  .nav-button {
    width: 30px;
    height: 30px;
    text-align: center;
    line-height: 30px;
    font-size: 24px;
    margin-right: 10px;
    display: none; /* 一开始隐藏图标 */
    cursor: pointer;
  }
</style>

<!-- logo开始 -->
<!--   省略部分html ，具体见前面 -->
<!-- logo开始 -->

<!-- 栏目图标开始 -->
<div class="nav-button iconfont icon-lanmu"></div>
<!-- 栏目图标结束 -->
```

- 一开始图标是隐藏的，当 **页面视口宽 <=992px** 再将图标显示 （ 以下代码要放在所有 css 之后）

```css
@media screen and (max-width: 992px) {
  .top nav {
    display: none; /* 隐藏导航 */
  }

  .nav-button {
    display: block; /* 显示导航按钮 */
  }
}
```

### 10、完整版代码

项目目录结构

```js
response-web
├─ .gitignore
├─ css
│  ├─ global.css
│  ├─ index.css
│  ├─ media.css
│  ├─ reset.css
│  ├─ response.css
│  └─ skin-theme.css   // 主题
├─ iconfont
│  ├─ demo.css
│  ├─ demo_index.html
│  ├─ iconfont.css
│  ├─ iconfont.js
│  ├─ iconfont.json
│  ├─ iconfont.ttf
│  ├─ iconfont.woff
│  └─ iconfont.woff2
├─ images  // 图片内容省略
├─ index.html
├─ js
│  └─ menu.js
└─ README.md
```

`index.html` 网站首页

```html
<!DOCTYPE html>
<!-- data-theme="yellow" -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>兼容多终端的响应式网站</title>
    <!-- 清除标签默认样式 -->
    <link rel="stylesheet" href="./css/reset.css" />
    <!-- 主题皮肤样式表 -->
    <link rel="stylesheet" href="./css/skin-theme.css" />
    <!-- 字体图标样式表 -->
    <link rel="stylesheet" href="./iconfont/iconfont.css" />
    <!-- 全局样式表 -->
    <link rel="stylesheet" href="./css/global.css" />
    <!-- 首页页面样式表 -->
    <link rel="stylesheet" href="./css/index.css" />
    <!-- 媒体查询 响应式栅格系统样式表 -->
    <link rel="stylesheet" href="./css/media.css" />
    <link rel="stylesheet" href="./css/response.css" />
  </head>
  <body>
    <header class="header">
      <div class="header-content">
        <!-- 网站头部开始 -->
        <div class="top" id="J_top">
          <div class="top-content layout">
            <!-- logo开始 -->
            <div class="logo">
              <a href="#">
                <img src="./images/logo.png" alt="艾编程logo" width="118" />
              </a>
            </div>
            <!-- logo结束 -->

            <!-- 栏目小图标 开始 -->
            <div class="nav-button iconfont icon-lanmu"></div>
            <!-- 栏目小图标 结束 -->
            <!-- 导航开始 -->
            <nav>
              <ul class="menu">
                <li>
                  <a href="">网站首页</a>
                </li>
                <li>
                  <a href="">国内游</a>
                  <dl class="menu-dropdown">
                    <dd><a href="#">北京</a></dd>
                    <dd><a href="#">三亚</a></dd>
                    <dd><a href="#">广东</a></dd>
                    <dd><a href="#">厦门</a></dd>
                    <dd><a href="#">云南</a></dd>
                  </dl>
                </li>
                <li>
                  <a href="">出镜游</a>
                  <dl class="menu-dropdown">
                    <dd><a href="#">泰国</a></dd>
                    <dd><a href="#">日本</a></dd>
                    <dd><a href="#">美国</a></dd>
                    <dd><a href="#">台湾</a></dd>
                    <dd><a href="#">海岛</a></dd>
                  </dl>
                </li>
                <li>
                  <a href="">周边游</a>
                  <dl class="menu-dropdown">
                    <dd><a href="#">北海</a></dd>
                    <dd><a href="#">桂林</a></dd>
                    <dd><a href="#">张家界</a></dd>
                    <dd><a href="#">凤凰</a></dd>
                  </dl>
                </li>
                <li>
                  <a href="">主题游</a>
                  <dl class="menu-dropdown">
                    <dd><a href="#">游学</a></dd>
                    <dd><a href="#">自组</a></dd>
                  </dl>
                </li>
                <li>
                  <a href="">自由行</a>
                  <dl class="menu-dropdown">
                    <dd><a href="#">三亚</a></dd>
                    <dd><a href="#">厦门</a></dd>
                    <dd><a href="#">丽江</a></dd>
                  </dl>
                </li>
                <li><a href="">合作案例</a></li>
                <li><a href="">关于我们</a></li>
              </ul>
            </nav>
            <!-- 导航结束 -->
          </div>
        </div>
        <!-- 网站头部结束 -->
      </div>
    </header>

    <!--js 代码一定要放在 /body 的最前-->
    <script src="./js/menu.js"></script>
  </body>
</html>
```

- `./css/skin-theme.css` 不同主题样式

```css
/* 主题皮肤定制 */
/* 默认主题写在上面 */

/* 绿色主题 */
:root,
html[data-theme="turquoise"] {
  /* 主色调 */
  --primary--color: #1ec28b; /* 主体色 */

  --light-gray-color: #f4f4f6; /* 浅灰色 */
  --white-color: #fff; /* 白色 */

  /* 字体色 */
  --font-black-color: #000; /* 黑色 */
  --font-dark-grey-color: #666; /* 深灰色 */
  --font-red-color: #ff0000; /* 红色 */
  --font-white-color: #fff; /* 白色 */

  /* 边框色 */
  --border-dark-grey-color: rgba(28, 28, 27, 0.22); /* 深灰色边框 */

  /* 辅助色 */
  --sub-dark-red-color: #ff6347; /* 深红色 */
  --sub-deep-orange-color: #ff8900; /* 深橘红色 */

  /* 网站底部色 */
  --footer-bg-color1: #2e2e2e; /* 网站底部背景色 */
  --footer-bg-color2: #212121; /* 网站底部背景色 */
  --footer-font-color: #d6d6d6; /* 网站底部背景色 */
}

/* 黄色主题 */
html[data-theme="yellow"] {
  /* 主色调 */
  --primary--color: #ffd336; /* 主体色 */
  --light-gray-color: #f4f4f6; /* 浅灰色 */
  --white-color: #fff; /* 白色 */

  /* 字体色 */
  --font-black-color: #000; /* 黑色 */
  --font-dark-grey-color: #666; /* 深灰色 */
  --font-red-color: #ff0000; /* 红色 */
  --font-white-color: #fff; /* 白色 */

  /* 边框色 */
  --border-dark-grey-color: rgba(28, 28, 27, 0.22); /* 深灰色边框 */

  /* 辅助色 */
  --sub-dark-red-color: #ff6347; /* 深红色 */
  --sub-deep-orange-color: #ff8900; /* 深橘红色 */

  /* 网站底部色 */
  --footer-bg-color1: #2e2e2e; /* 网站底部背景色 */
  --footer-bg-color2: #212121; /* 网站底部背景色 */
  --footer-font-color: #d6d6d6; /* 网站底部背景色 */
}

/* 深红色主题 */
html[data-theme="red"] {
  /* 主色调 */
  --primary--color: #ff383f; /* 主体色 */
  --light-gray-color: #f4f4f6; /* 浅灰色 */
  --white-color: #fff; /* 白色 */

  /* 字体色 */
  --font-black-color: #000; /* 黑色 */
  --font-dark-grey-color: #666; /* 深灰色 */
  --font-red-color: #ff0000; /* 红色 */
  --font-white-color: #fff; /* 白色 */

  /* 边框色 */
  --border-dark-grey-color: rgba(28, 28, 27, 0.22); /* 深灰色边框 */

  /* 辅助色 */
  --sub-dark-red-color: #ff6347; /* 深红色 */
  --sub-deep-orange-color: #ff8900; /* 深橘红色 */

  /* 网站底部色 */
  --footer-bg-color1: #2e2e2e; /* 网站底部背景色 */
  --footer-bg-color2: #212121; /* 网站底部背景色 */
  --footer-font-color: #d6d6d6; /* 网站底部背景色 */
}
```

- `./css/reset.css` 清除标签默认样式

```css
/* 清除默认样式*/
html,
body,
ul,
li,
dl,
dt,
dd {
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
}
a {
  text-decoration: none; /* 去掉 a标签默认的下划线 */
}
```

- `./css/global.css` 全局通用样式

```css
/* 全局通用样式 */
body {
  font: 16px/1.5 "微软雅黑";
  color: #000;
}

.layout {
  max-width: 1200px; /* 最大宽度 */
  margin: 0 auto;
}
```

- `./css/response.css` 响应式样式

```css
/* 当浏览器的宽度小于等于 992px */
@media screen and (max-width: 992px) {
  /* 隐藏顶部导航 */
  .top nav {
    display: none;
  }
  /* 显示栏目图标 */
  .nav-button {
    display: block;
  }
}
```

- `./css/index.css` 首页样式

```css
/* 当前项目首页用到的 css 样式 */
.header {
  width: 100%;
  height: 758px;
  /* background-image: linear-gradient(
    to bottom,
    var(--primary--color),
    var(--white-color)
    ); */
  /* opacity: 0.4; 设置元素透明 */
  position: relative; /* 相对定位 */
}
.header::before,
.header-content {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
.header::before {
  content: "";
  background-image: linear-gradient(
    to bottom,
    var(--primary--color),
    var(--white-color)
  );
  opacity: 0.4;
}

.top {
  /* width:100%; */
  height: 80px;
  /* background-color: #ddd; */
  /* border: 1px solid red; */
}

.top .top-content {
  height: inherit;
  /* background-color: red; */
  display: flex;
  align-items: center;
  justify-content: space-between; /* 水平两端对齐 */
}
.top .top-content ul.menu {
  display: flex;
}

/* 一级导航样式 */
ul.menu li a {
  display: block;
  line-height: 80px;
  padding-right: 16px;
  padding-left: 15px;
  color: var(--font-black-color);
  font-size: 18px;
  /* border: 1px solid red; */
}
ul.menu li a:hover {
  color: var(--primary--color);
}
ul.menu li {
  position: relative; /* 相对定位 */
}
ul.menu li::after {
  content: "";
  position: absolute;
  bottom: 0px;
  left: 50%;
  right: 50%;
  height: 2px;
  background-color: var(--primary--color);
  transition: left 0.3s, right 0.3s;
}
ul.menu li:hover::after {
  left: 0;
  right: 0;
}

/* 二级下拉菜单 */
ul.menu li .menu-dropdown {
  position: absolute;
  left: 0;
  right: 0;
  top: 80px;
  background-color: var(--white-color);
  transform-origin: top center; /* 变换的原点在顶部的中心 */
  transform: scaleY(0); /* y轴缩小到0 看不到了*/
  transition: transform 0.3s; /* 过渡效果 */
}
ul.menu li .menu-dropdown {
  padding-top: 2px;
  padding-bottom: 8px;
}
ul.menu li .menu-dropdown dd {
  overflow: hidden;
}
ul.menu li .menu-dropdown dd a {
  line-height: 30px;
  padding: 0px;
  text-align: center;
  /* border: 1px solid red; */
  position: relative; /* 相对定位 */
  transition: transform 0.5s;
}
ul.menu li:hover .menu-dropdown {
  transform: scaleY(1); /* y轴放大到1 显示出正常大小 */
}
/* 绘制小竖线 */
.menu-dropdown dd a::before {
  content: "";
  position: absolute;
  top: 7px;
  bottom: 7px;
  left: 10px;
  width: 2px;
  background-color: var(--primary--color);
  display: none; /*隐藏*/
}
/* 鼠标移入 a标签向右移动 10px */
.menu-dropdown dd:hover a {
  transform: translateX(10px);
}
/* 鼠标移入显示竖线 */
.menu-dropdown dd:hover a::before {
  display: block;
}
.sticky {
  width: 100%;
  position: fixed;
  top: 0;
  background-color: var(--white-color);
  box-shadow: 0 2px 5px var(--border-dark-grey-color);
  /* 定义 animation 动画 */
  animation: sticky-animation 0.5s ease-out both;
}

@keyframes sticky-animation {
  0% {
    opacity: 0; /* 透明的 */
    transform: translateY(-100%); /* 向上移动自身的高度 */
  }
  100% {
    opacity: 1; /* 不透明 */
    transform: translateY(0); /* 向下移动到自身的高度 */
  }
}

/* 栏目图标样式 */
.nav-button {
  width: 34px;
  /* background: red; */
  margin-right: 10px;
  font-size: 30px;
  text-align: center;
  display: none;
}
```

- `./js/menu.js` 实现吸顶盒导航

```js
function stickyMenu() {
  // 获取 top元素
  const _top = document.getElementById("J_top");
  // 监听浏览器的滚动事件
  window.addEventListener("scroll", function () {
    // 获取当前滚动条滚动的距离
    let scrollTop =
      document.documentElement.scrollTop || document.body.scrollTop;
    if (scrollTop > 1) {
      // 就给 top 元素添加 sticky 类名
      _top.classList.add("sticky");
    } else {
      _top.classList.remove("sticky");
    }
  });
}
stickyMenu(); // 调用函数
```

### 11、修复 bug 一

当页面宽度 <=1200px 时 ,logo 图标与浏览器左边添加 25px 的间距

```css
/* 以下代码放入 response.css 文件中 */
@media screen and (max-width: 1200px) {
  .logo {
    margin-left: 25px;
    /* 如果需要过渡自然的活，可以加上过渡动画 */
  }
}
```

### 12、修复 bug 二

栏目小图标按设计稿要求，他与浏览器左边的间距为 30px

```css
.nav-button {
  /* 省略部分css -- */
  margin-right: 30px; /* 这里的右边距为 30px */
  cursor: pointer; /* 鼠标样式-手指形状 */
}
```

## 五、垂直二级导航开发

TIP

- 当浏览器屏幕缩小到 `<=992px` 时，水平导航会隐藏，从而在最右侧显示栏目小图标 ![image-20250113175039595](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAdCAIAAABE/PnQAAABOUlEQVRIibWWwU3DQBBF39+sEEfSVUgHFJBOSAcgIaUAKoBUENogZ8LR989hvbGTWFx2PIev0bc1X+uZP159dN8ABl1iiWY+YTAuzxjlQXxGgDQSjc3zhegMmBFCnvioDuEz7j/XrX4In6UyAafDZr19P9EWy6e3l91qOWKyXQUX943VgbuFXSuW0Gd3bK/7T6SiZ5uqHZv3PeixHCo0z9gg4zpcfV7eaeczveZIedgsAXyq8+objOGLk7F+vzbr5wgfvO5WD5LAkiAxtDwkbIMH1L47MrXSo/J0NrLBHnZKFJ/LKlJt/BW282liHEIxjU8wB6ahI1cYxGeKrfVzCPPB41IWsiyU+j9akAsAzhWNsfbdsS6mWTBdKM6Q534XauRBjY7bzGfb9YYxeRdp5eutoihP+LOV/wPi+OgEPRkiEAAAAABJRU5ErkJggg==)。（这个功能我们在上一小节《网站顶部导航》已经实现了）。
- 点击右侧栏目小图标 ![image-20250113175039595](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAdCAIAAABE/PnQAAABOUlEQVRIibWWwU3DQBBF39+sEEfSVUgHFJBOSAcgIaUAKoBUENogZ8LR989hvbGTWFx2PIev0bc1X+uZP159dN8ABl1iiWY+YTAuzxjlQXxGgDQSjc3zhegMmBFCnvioDuEz7j/XrX4In6UyAafDZr19P9EWy6e3l91qOWKyXQUX943VgbuFXSuW0Gd3bK/7T6SiZ5uqHZv3PeixHCo0z9gg4zpcfV7eaeczveZIedgsAXyq8+objOGLk7F+vzbr5wgfvO5WD5LAkiAxtDwkbIMH1L47MrXSo/J0NrLBHnZKFJ/LKlJt/BW282liHEIxjU8wB6ahI1cYxGeKrfVzCPPB41IWsiyU+j9akAsAzhWNsfbdsS6mWTBdKM6Q534XauRBjY7bzGfb9YYxeRdp5eutoihP+LOV/wPi+OgEPRkiEAAAAABJRU5ErkJggg==) ，会显示对应的二级菜单 ，效果如下

> 以下是具体的实现步骤

### 1、第一步：实现黑色半透明遮罩层

![image-20250114121218995](https://www.arryblog.com/assets/img/image-20250114121218995.8b8d21ad.png)

黑色半透明遮罩层特点

- 黑色半透明遮罩层的大小与浏览器屏幕一样大小，并且覆盖在页面其它内容的最上面。
- 当我们滚动浏览器的滚动条时，黑色半透明遮罩层位置始终相对于浏览器固定不动。

> 通过上面的分析，我们知道，黑色半透明遮罩层是相对于浏览器固定定位，定位在浏览器的左上角。

### 1.1、具体实现

TIP

- 创建一个 class 类名为 `mask` 的 div 作为 body 标签 的子元素，将其宽高设置与浏览器一样大小，同时背景为黑色半透明
- 利用 `fixed` 固定定位，将其定位在浏览器的左上角

```html
<style>
  /*  黑色半透明遮罩层 */
  .mask {
    position: fixed; /* 固定定位 */
    /* 
        top 与 bottom 拉伸盒子高与浏览器一样高
        left 与 right 拉伸盒子宽与浏览器一样高
        */
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

    /* 这里的黑色半透明可以直接用 ` rgba(0,0,0,.5)` 实现 ，因为在任何主题下，遮罩层都是黑色的半透明的，不会被改成其它颜色*/
    background-color: rgba(0, 0, 0, 0.3);
    /* 一般我们会给黑色的半透明遮罩层添加  保证他会在的所有其它元素的最上面显示，不过在这个项目中，垂直菜单容器要在他上面显示*/
    z-index: 99;
  }
</style>

<!-- 黑色半透明遮罩层 开始 -->
<div class="mask"></div>
<!-- 黑色半透明遮罩层 结束 -->
```

### 2、第二步：制作垂直导航最外层黑色半透明容器

![image-20250114123639915](https://www.arryblog.com/assets/img/image-20250114123639915.5c23611d.png)

- 制作一个黑色的半透明遮罩层，宽 `420px` ，高同浏览器一样高。
- 利用固定定位，将遮罩层定位在浏览器顶部的最左边

温馨注意：

- 虽然 `.mobile-nav` 元素是放在绝对定位元素 `.header-content` 中，但他还是在默认的 html 层叠上下文中。因为 `.header-content` 是的 z-index 值是 auto，并不会创建自己的层叠上下文。
- `.mask` 黑色半透明遮罩层是在 html 层叠上下文中，他写在`</body>`的前面，所以会覆盖在`.mobile-nav` 黑色半透明遮罩层上面，我们需要给`.mobile-nav` 元素 设置 `z-index` 来提升他的层级

```html
<style>
  /* 移动端或 ipad 端 导航*/
  nav.mobile-nav {
    width: 420px;
    position: fixed; /* 固定定位 */
    left: 0;
    top: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.3);
    z-index: 100; /* 提升层级，让他显示在黑色半透明遮罩层的上面，这里的值一定要大于 .mask 选择器中 z-index的值  */
  }
</style>

<!-- 以下代码放在 class="header-content" div 容器中 -->

<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav"></nav>
<!-- 移动 或 ipad端导航 结束-->
```

### 3、第三步、制作导航关闭按扭

![image-20250114130753435](https://www.arryblog.com/assets/img/image-20250114130753435.25afa29b.png)

- 制作一个宽高为 `50px` 的小正方形，相对父元素 `.mobile-nav` 绝对定位，定位在与父元素上和右都为 30px 的位置
- 利用 iconfont 阿里图标，给元素添加 关闭按扭的图标，将图标颜色设为白色

温馨提示

这里一定要将 `line-height` 行高的值设为 1 ，否则就会继承 `body` 选择器中的 `line-height` 值 1.5

```html
<style>
  .colse-button {
    position: absolute;
    top: 30px;
    right: 30px;
    width: 50px;
    height: 50px;
    font-size: 50px;
    line-height: 1; /* 记得将行高设为 1 */
    color: #fff;
    cursor: pointer;
  }
</style>

<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav">
  <!-- 关闭按扭用的 iconfont 图标 -->
  <span class="colse-button iconfont icon-chacha1"></span>
</nav>
<!-- 移动 或 ipad端导航 结束-->
```

### 4、第四步：垂直二级导航的显示与隐藏

![GIF2025-1-1418-08-20](https://www.arryblog.com/assets/img/GIF2025-1-1418-08-20.def327d6.gif)

- 一开始遮罩层和移动导航容器都是隐藏的

```css
/* 黑色半透明遮罩层 */
.mask {
  display: none;
}

/* 移动端或 ipad 端 导航*/
nav.mobile-nav {
  display: none;
}
```

- 给栏目小图标添加 `id="J_nav-icon"`方便 JS 获取该元素
- 给关闭按扭添加`id='J_close-button'`方便 JS 获取该元素
- 给全屏的黑色半透明遮罩层添加 `id="J_mask"` ，方便 JS 获取该元素
- 给垂直菜单添加 `id="J_mobile-nav"` ，方便 JS 获取该元素

```html
<!-- 栏目小图标 开始 -->
<div class="nav-button iconfont icon-lanmu" id="J_nav-icon"></div>

<!-- 关闭按扭用的 iconfont 图标 -->
<span class="colse-button iconfont icon-chacha1" id="J_close-button"></span>

<!-- 黑色半透明遮罩层 开始 -->
<div class="mask" id="J_mask"></div>

<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav" id="J_mobile-nav"></nav>
```

- JS 实现点击 栏目小图标显示菜单和黑色半透明遮罩层
- JS 实现点击关闭按扭，关闭 垂直导航和黑色半透明遮罩层

```js
// 获取栏目小图标
const navIcon = document.getElementById("J_nav-icon");
// 获取关闭菜单按扭
const closeButton = document.getElementById("J_close-button");
// 获取遮罩层
const mask = document.getElementById("J_mask");
// 获取垂直导航
const mobileNav = document.getElementById("J_mobile-nav");

// 给栏目小图标添加点击事件
navIcon.addEventListener("click", function () {
  // 显示黑色半 透明遮罩层
  mask.style.display = "block";
  // 显示菜单
  mobileNav.style.display = "block";
});

// 给关闭菜单按扭添加点击事件
closeButton.addEventListener("click", function () {
  // 关闭菜单
  mask.style.display = "none";
  mobileNav.style.display = "none";
});
```

### 5、第五步：添加一级菜单

![image-20250114142558613](https://www.arryblog.com/assets/img/image-20250114142558613.1c56d73f.png)

- 设置菜单项与黑色遮罩层顶部，左边，右边的间距
- 设置每一个菜单项的字体样式 和 间距

```html
<style>
  /* 清除 h3 标签的默认外边距 */
  h3 {
    margin: 0;
    padding: 0;
  }
  .nav-list {
    padding-top: 92px;
    margin: 0px 30px;
  }
  .nav-list li h3,
  .nav-list li > a {
    display: block;
    font-size: 32px;
    color: #fff;
    font-weight: 400;
    margin-bottom: 20px;
    /* 行高 32 *1.5= 48px  通过行高 推出高为 48px */
    /* height: 48px; */
    cursor: pointer;
  }
</style>

<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav">
  <span class="colse-button iconfont icon-chacha1"></span>
  <ul class="nav-list">
    <li><a href="#">首页</a></li>
    <li><h3>国内游</h3></li>
    <li><h3>出镜游</h3></li>
    <li><h3>周边游</h3></li>
    <li><h3>主题游</h3></li>
    <li><h3>自由行</h3></li>
    <li><h3>合作案例</h3></li>
    <li><h3>关于我们</h3></li>
  </ul>
</nav>
<!-- 移动 或 ipad端导航 结束-->
```

### 6、第六步：为一级菜单添加向右的箭头

![image-20250114144428631](https://www.arryblog.com/assets/img/image-20250114144428631.86a1f876.png)

- 利用 span 标签 和 iconfont 图标来实现向右的箭头。
- 箭头相对于父元素绝对定位，定位到距离父元素右侧 31px ，垂直居中位置

```html
<style>
  .nav-list li h3 {
    position: relative; /* 相对定位 */
  }
  .nav-list li h3 span.arrow {
    /* 不要设置宽和高 阿里图标形成的图片本身占居空间是一个正方形*/
    position: absolute; /* 绝对定位 */
    right: 31px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 28px;
    line-height: 1; /* 行高为 1 */
  }
</style>

<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav">
  <span class="colse-button iconfont icon-chacha1"></span>
  <ul class="nav-list">
    <li><a href="#">首页</a></li>
    <li>
      <h3>
        国内游
        <span class="arrow iconfont icon-youjiantou2"></span>
      </h3>
    </li>
    <li>
      <h3>出镜游<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li>
      <h3>周边游<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li>
      <h3>主题游<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li>
      <h3>自由行<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li><h3>合作案例</h3></li>
    <li><h3>关于我们</h3></li>
  </ul>
</nav>
<!-- 移动 或 ipad端导航 结束-->
```

### 7、第七步：二级菜单展开始，箭头朝下的实现原理

![image-20250114145615069](https://www.arryblog.com/assets/img/image-20250114145615069.c82b494b.png)

当点击按扭，展开二级菜单时，我们给 `span` 标签再添加一个为 `arrow-up` 的 class 类名，这个类名用来控制箭头向下。

```html
<style>
  .nav-list li h3 span.arrow {
    /* 省略部分 CSS 样式，具体见前面*/
    transition: transform 0.3s; /* 添加过渡动画 */
  }
  .nav-list li h3 span.arrow-down {
    /* 在原来位移的基础上，再顺时间旋转 90deg */
    transform: translateY(-50%) rotate(90deg);
  }
</style>

<h3>
  国内游
  <span class="arrow iconfont icon-youjiantou2 arrow-down"></span>
</h3>
```

### 8、第八步：添加二级菜单

![image-20250114151645161](https://www.arryblog.com/assets/img/image-20250114151645161.f1e8ac13.png)

温馨提示

在一级菜单中，我们给 a 标签添加的样式，会影响到这里，所以记得去做相关修改

```html
<style>
  /* 垂直二级菜单 */
  .mobile-nav .nav-list li .menu-dropdown dd a {
    display: block;
    height: 64px;
    line-height: 64px;
    font-size: 32px;
    margin-bottom: 0px;
    color: #fff;
    text-indent: 64px;
  }
  .mobile-nav .nav-list li .menu-dropdown dd a:hover {
    background-color: var(--primary-color);
  }
</style>

<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav">
  <span class="colse-button iconfont icon-chacha1"></span>
  <ul class="nav-list">
    <li><a href="#">首页</a></li>
    <li>
      <h3>
        国内游
        <span class="arrow iconfont icon-youjiantou2 arrow-down"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">北京</a></dd>
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">广东</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">云南</a></dd>
      </dl>
    </li>
    <li>
      <h3>出镜游<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li>
      <h3>周边游<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li>
      <h3>主题游<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li>
      <h3>自由行<span class="arrow iconfont icon-youjiantou2"></span></h3>
    </li>
    <li><h3>合作案例</h3></li>
    <li><h3>关于我们</h3></li>
  </ul>
</nav>
<!-- 移动 或 ipad端导航 结束-->
```

### 9、第九步：二级菜单展开 和 收缩 动画的实现原理

![image-20250114154454675](https://www.arryblog.com/assets/img/image-20250114154454675.27285694.png)

- 当点击一级菜单，会向下慢慢展开显示二级菜单，本质是在不断的改变 `li`元素的高度。
- 一开始，**每个 li 的高度= h3 元素高 + `margin-bottom` 值 ** ，然后针对溢出 li 部分隐藏。
- 当点击一级菜单时，动态计算当前`li` 的高度，然后修改 li 的高度。

> 每个 li 展开后高 = h3 元素高 + 20px 的 margin-bottom + dl 元素的占位高
>
> li 展开后的高度，需要通过 JS 来自动计算。

```css
.nav-list li {
  height: 68px;
  overflow: hidden;
  transition: height 0.3s; /* 为高度属性添加过渡动画 */
}
<!-- 移动 或 ipad端导航 开始-->
<nav class="mobile-nav">
  <span class="colse-button iconfont icon-chacha1"></span>
  <ul class="nav-list">
    <li><a href="#">首页</a></li>
    <li>
      <h3>
        国内游
        <span class="arrow iconfont icon-youjiantou2 arrow-down"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">北京</a></dd>
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">广东</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">云南</a></dd>
      </dl>
    </li>
    <li>
      <h3>出镜游<span class="arrow iconfont icon-youjiantou2"></span></h3>
      <dl class="menu-dropdown">
        <dd><a href="#">泰国</a></dd>
        <dd><a href="#">日本</a></dd>
        <dd><a href="#">美国</a></dd>
        <dd><a href="#">台湾</a></dd>
        <dd><a href="#">海岛</a></dd>
      </dl>
    </li>
    <li>
      <h3>周边游<span class="arrow iconfont icon-youjiantou2"></span></h3>
      <dl class="menu-dropdown">
        <dd><a href="#">北海</a></dd>
        <dd><a href="#">桂林</a></dd>
        <dd><a href="#">张家界</a></dd>
        <dd><a href="#">凤凰</a></dd>
      </dl>
    </li>
    <li>
      <h3>主题游<span class="arrow iconfont icon-youjiantou2"></span></h3>
      <dl class="menu-dropdown">
        <dd><a href="#">游学</a></dd>
        <dd><a href="#">自组</a></dd>
      </dl>
    </li>
    <li>
      <h3>自由行<span class="arrow iconfont icon-youjiantou2"></span></h3>
      <dl class="menu-dropdown">
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">丽江</a></dd>
      </dl>
    </li>
    <li><h3>合作案例</h3></li>
    <li><h3>关于我们</h3></li>
  </ul>
</nav>
<!-- 移动 或 ipad端导航 结束-->
```

### 10、第十步：JS 实现二级菜单特效 - 事件委托

TIP

- 当我们点击 h3 标签时，才会展开和收缩二级菜单，不过这里我们不打算给 h3 绑定点击事件。
- 我们采用事件委托，将 h3 的点击事件委托给到他们共同的父元素 ul 来实现。

**具体实现步骤**

- 给 `<ul class="nav-list">` 添加`id="J_mobile-nav-list"` 方便通过 Id 名来获取 ul 元素

```html
<ul class="nav-list" id="J_mobile-nav-list">
  <!-- 省略更多的 html 标签  -->
</ul>
```

- 采用事件代理，将 h3 的点击事件委托给到 ul

```js
// 获取 ul 元素
const mobileNavList = document.getElementById("J_mobile-nav-list");
// 添加点击事件
mobileNavList.addEventListener("click", function (e) {
  const target = e.target; // 获取触发事件的元素
  // 如果触发事件的元素标签名不是 h3 则 啥也不做
  if (target.tagName.toLowerCase() !== "h3") return;

  // 如果触发事件的元素标签名是 h3，则执行这行注释之后的代码
});
```

### 11、第十一步： 如何判断当前菜单是展开还是折叠的

TIP

我们需要给每项菜单的 li 或 h3 标签的 S 对象添加一个属性 flag ，这个属性记录着当前的菜单状态

- 如果 `flag 值为 false` 则表示当前菜单折叠
- 如果 `flag 值为 true` 则表示当前菜单是展开的

```js
// 获取 ul 元素
const mobileNavList = document.getElementById("J_mobile-nav-list");
// 添加点击事件
mobileNavList.addEventListener("click", function (e) {
  const target = e.target; // 获取触发事件的元素
  if (target.tagName.toLowerCase() !== "h3") return;

  // ---------------------- 新增JS ----------------------------------
  // 如果 target.flag 值为 false 或 undefined
  if (!target.flag) {
    // 当前菜单是折叠的，则可以展开
    // 更新菜单状态
    target.flag = true;
    alert("可以展开");
    // 菜单展开，本质就是动态修改 li 的高度，
    // 同给 span.arrow  元素添加 class 类名 arrow-down
  } else {
    // 当前菜单是展开的，可以折叠
    // 更新菜单状态
    target.flag = false;
    alert("可以折叠");
  }
});
```

### 12、第十二步：实现菜单展开和折叠

![GIF2025-1-1417-53-04](https://www.arryblog.com/assets/img/GIF2025-1-1417-53-04.f700da0b.gif)

**菜单展开** ：

- 通过 JS 计算当前 li 展开后的高度 ，然后修改当前 li 的高
  - li 展开后高 = h3 的高 + h3 元素的 margin-bottom 值 + dl 元素的高（dl 元素没有外边距）
- h3 标签中的 span 元素添加 class 类名 `arrow-down` ，实现 箭头向下

**菜单收缩**：

- li 收缩后高度 = h3 的高 + h3 元素的 margin-bottom 值
- 移除 h3 标签中的 span 元素的 class 类名 `arrow-down` ，实现箭头向右

```js
// 获取 ul 元素
const mobileNavList = document.getElementById("J_mobile-nav-list");
// 添加点击事件
mobileNavList.addEventListener("click", function (e) {
  const target = e.target; // 获取触发事件的元素
  if (target.tagName.toLowerCase() !== "h3") return;

  // 如果 target.flag 值为 false 或 undefined
  if (!target.flag) {
    // 当前菜单是折叠的，则可以展开
    // 更新菜单状态
    target.flag = true;

    // ---------------------- 新增JS ----------------------------------
    // 获取 h3 标签可视高 （包括 height +padding +border)
    const h3Height = target.offsetHeight;
    // 获取 h3 标签的向下外边距
    const marginBottom = parseInt(window.getComputedStyle(target).marginBottom);
    // 获取当前菜单二级菜单 dl 可视高 （dl 没有外边距）
    const dlHeight = target.nextElementSibling.offsetHeight;
    // 计算得到当前 li的高度
    const liHeight = h3Height + marginBottom + dlHeight;
    // 更新当前菜单 li 的高度
    target.parentNode.style.height = `${liHeight}px`;
  } else {
    // 当前菜单是展开的，可以折叠
    // 更新菜单状态
    target.flag = false;

    // ---------------------- 新增JS ----------------------------------
    // 获取 h3 标签可视高 （包括 height +padding +border)
    const h3Height = target.offsetHeight;
    // 获取 h3 标签的向下外边距
    const marginBottom = parseInt(window.getComputedStyle(target).marginBottom);
    // 计算得到当前 li的高度
    const liHeight = h3Height + marginBottom;
    // 更新当前菜单 li 的高度
    target.parentNode.style.height = `${liHeight}px`;
  }
});
```

### 13、第十三步：垂直二级导航移动端适配

![GIF2025-1-1417-51-50](https://www.arryblog.com/assets/img/GIF2025-1-1417-51-50.cd29182a.gif)

移动端二级导航的各种尺寸与 ipad 端不同，我们有以下两种方式来适配

### 13.1、适配方式一

TIP

通过媒体查询来检测当前视口宽，如果视口宽<=576px 时，则重新定义 CSS 的属性值

```css
/* 以下 css 放在 response.css 文件中 */
/* 当页面宽度小于 576px 时，对应的菜单样式 */
@media screen and (max-width: 576px) {
  /* 垂直导航容器- ipad端或移动端导航*/
  nav.mobile-nav {
    width: 280px;
  }
  /* 关闭按扭 */
  .close-button {
    width: 30px;
    height: 30px;
    font-size: 30px;
  }
  .nav-list {
    padding-top: 54px;
    margin: 0 30px;
  }
  .nav-list li h3,
  .nav-list li a {
    font-size: 18px;
    /* height:27px; */
    /* 行高 1.5 * 18 = 27px  向上 4 或 5
        */
    margin-bottom: 10px;
  }
  .nav-list li {
    height: 37px; /* 导航收缩时的高度*/
  }
  /* 
    需要动态的计算当前 li的高度 
    收缩时 li高度 = h3 高度 + h3 的margin-bottom   =64px 
    展开时 li高度=h3 高度 + h3 的margin-bottom + dl可视区高
    */

  /* 箭头样式 */
  .nav-list li h3 span.arrow {
    /* border: 1px solid red; */
    font-size: 17px;
    right: 29px;
  }

  /* 移动端 二级导航样式 */
  .mobile-nav .menu-dropdown dd a {
    display: block;
    height: 36px;
    line-height: 36px;
    text-indent: 35px;
  }
  .mobile-nav .menu-dropdown {
    /* 27-9-4 */
    padding-bottom: 14px;
  }
}
```

### 13.2、适配方式二

- 在 :root 选择器中，将不同的属性值，定义成一套 CSS 自定义属性

```css
/* 以下 css 放在 skin-theme.css 文件中 */
:root {
  --nav-width: 420px; /* 导航容器宽 */
  --close-button-width: 50px; /* 关闭按钮宽 */
  --close-button-height: 50px; /* 关闭按钮高 */
  --close-button-font-size: 50px; /* 关闭按钮字体大小 */
  --close-button-right: 30px; /* 关闭按钮距父元素右距离 */
  --close-button-top: 30px; /* 关闭按钮距父元素上距离 */
  --nav-top: 92px; /* 整个菜单距顶部距离 */
  --nav-margin-left: 30px; /* 整个菜单左外边距 */
  --nav-margin-right: 30px; /* 整个菜单右外边距*/
  --menu-item-font-size: 32px; /* 菜单项字体大小 */
  --menu-item-margin-bottom: 16px; /* 菜单项底部外边距 */
  --menu-item-height: 64px; /* 菜单项高 */
  --arrow-font-size: 28px; /* 箭头字体大小 */
  --arrow-right: 41px; /* 箭头距父元素右距离 */
  --submenu-item-height: 64px; /* 子菜单项高 */
  --submenu-item-font-size: 32px; /* 子菜单项字体大小 */
  --submenu-item-text-indent: 60px; /* 子菜单项文本缩进 */
  --submenu-item-padding-bottom: 16px; /* 子菜单项底部外边距 */
}
```

- 通过媒体查询来检测当前视口宽，如果视口宽<=576px 时，则重新定义一套 CSS 自定义属性

```css
/* 以下 css 放在 skin-theme.css 文件中 */
@media screen and (max-width: 576px) {
  :root {
    --nav-width: 280px;
    --close-button-width: 30px; /* 关闭按钮宽 */
    --close-button-height: 30px; /* 关闭按钮高 */
    --close-button-font-size: 30px; /* 关闭按钮字体大小 */
    --close-button-right: 30px; /* 关闭按钮距父元素右距离 */
    --close-button-top: 30px; /* 关闭按钮距父元素上距离 */
    --nav-top: 54px;
    --nav-margin-left: 30px; /* 整个菜单左外边距 */
    --nav-margin-right: 30px; /* 整个菜单右外边距*/
    --menu-item-font-size: 18px;
    --menu-item-margin-bottom: 10px; /* 菜单项底部外边距 */
    --menu-item-height: 37px; /* 菜单项高 */
    --arrow-font-size: 17px; /* 箭头字体大小 */
    --arrow-right: 29px;
    --submenu-item-height: 36px; /* 子菜单项高 */
    --submenu-item-line-height: 36px; /* 子菜单项高 */
    --submenu-item-font-size: 18px; /* 子菜单项字体大小 */
    --submenu-item-text-indent: 35px; /* 子菜单项文本缩进 */
    --submenu-item-padding-bottom: 14px; /* 子菜单项底部外边距 */
  }
}
```

- 将 CSS 代码中的属性值替换为 `var` 函数引用 CSS 自定义属性值

> 以下 CSS 和 上面的 自定义 CSS 属性 是当前效果完整 CSS

```css
/* 黑色半透明遮罩层样式 */
.mask {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 99; /* 遮罩层在最上层 */
  display: none; /* 隐藏*/
}

/* 垂直导航容器- ipad端或移动端导航*/
nav.mobile-nav {
  /* width: 420px; */
  width: var(--nav-width);
  position: fixed;
  left: 0;
  top: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 100; /* 导航要在遮罩层的上面 */
  display: none; /*隐藏*/
}
/* 关闭按扭 */
.close-button {
  display: block;
  width: var(--close-button-width);
  height: var(--close-button-height);
  font-size: var(--close-button-font-size);
  /* width: 50px; */
  /* height: 50px; */
  /* font-size: 50px; */
  line-height: 1;
  /* background-color: red; */
  color: #fff;
  position: absolute;
  /* right: 30px; */
  right: var(--close-button-right);
  /* top: 30px; */
  top: var(--close-button-top);
  cursor: pointer;
}
.nav-list {
  /* padding-top: 92px; */
  padding-top: var(--nav-top);
  /* margin: 0 30px; */
  margin: 0 var(--nav-margin-right) 0 var(--nav-margin-left);
}
.nav-list li h3,
.nav-list li a {
  display: block;
  /* font-size: 32px; */
  font-size: var(--menu-item-font-size);
  /* height:48px; */
  /* 行高 1.5 * 32 = 48px;  (48-32)/2= 8
    32-16=16px
    */
  /* margin-bottom: 16px; */
  margin-bottom: var(--menu-item-margin-bottom);
  color: #fff;
  font-weight: 400;
  cursor: pointer;
}
.nav-list li {
  /* height: 64px; 导航收缩时的高度 */
  height: var(--menu-item-height);
  overflow: hidden;
  transition: height 0.3s; /* 过渡动画 */
}
/*
需要动态的计算当前 li的高度
收缩时 li高度 = h3 高度 + h3 的margin-bottom   =64px
展开时 li高度=h3 高度 + h3 的margin-bottom + dl可视区高
*/
.nav-list li h3 {
  position: relative;
}
/* 箭头样式 */
.nav-list li h3 span.arrow {
  /* border: 1px solid red; */
  /* font-size: 28px; */
  font-size: var(--arrow-font-size);
  line-height: 1;
  position: absolute;
  /* right: 41px; */
  right: var(--arrow-right);
  top: 50%;
  transform: translateY(-50%);
}
/* 向下箭头的样式 */
.nav-list li h3 span.arrow-down {
  transform: translateY(-50%) rotate(90deg);
}

/* 移动端 二级导航样式 */
.mobile-nav .menu-dropdown dd a {
  display: block;
  /* height: 64px; */
  height: var(--submenu-item-height);
  /* line-height: 64px; */
  line-height: var(--submenu-item-line-height);
  /* text-indent: 60px; */
  text-indent: var(--submenu-item-text-indent);
  font-size: var(--submenu-item-font-size);

  margin-bottom: 0;
}
.mobile-nav .menu-dropdown {
  /* padding-bottom: 12px; */
  padding-bottom: var(--submenu-item-padding-bottom);
}
.mobile-nav .menu-dropdown dd a:hover {
  background-color: var(--primary--color);
}
```

### 14、完整的源码

```html
<!-- ipad端或移动端导航 开始-->
<nav class="mobile-nav" id="J_mobile-nav">
  <span class="close-button iconfont icon-chacha1" id="J_close-button"></span>

  <ul class="nav-list" id="J_moible-nav-list">
    <li><a href="#">首页</a></li>
    <li>
      <h3>
        国内游
        <span class="arrow iconfont icon-youjiantou2"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">北京</a></dd>
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">广东</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">云南</a></dd>
      </dl>
    </li>
    <li>
      <h3>
        出镜游
        <span class="arrow iconfont icon-youjiantou2"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">泰国</a></dd>
        <dd><a href="#">日本</a></dd>
        <dd><a href="#">美国</a></dd>
        <dd><a href="#">台湾</a></dd>
        <dd><a href="#">海岛</a></dd>
      </dl>
    </li>
    <li>
      <h3>
        周边游
        <span class="arrow iconfont icon-youjiantou2"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">北海</a></dd>
        <dd><a href="#">桂林</a></dd>
        <dd><a href="#">张家界</a></dd>
        <dd><a href="#">凤凰</a></dd>
      </dl>
    </li>
    <li>
      <h3>
        主题游
        <span class="arrow iconfont icon-youjiantou2"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">游学</a></dd>
        <dd><a href="#">自组</a></dd>
      </dl>
    </li>
    <li>
      <h3>
        自由行
        <span class="arrow iconfont icon-youjiantou2"></span>
      </h3>
      <dl class="menu-dropdown">
        <dd><a href="#">三亚</a></dd>
        <dd><a href="#">厦门</a></dd>
        <dd><a href="#">丽江</a></dd>
      </dl>
    </li>
    <li><a href="#">合作案例</a></li>
    <li><a href="#">关于我们</a></li>
  </ul>
</nav>
<!-- ipad端或移动端导航 结束-->

<!-- 黑色半透明遮罩层开始 -->
<div class="mask" id="J_mask"></div>
<!-- 黑色半透明遮罩层结束-->
subMenu();
function subMenu() {
  // 获取栏目小图标
  const navIcon = document.getElementById("J_nav-icon");
  // 获取遮罩层
  const mask = document.getElementById("J_mask");
  // 获取垂直导航容器
  const mobileNav = document.getElementById("J_mobile-nav");

  // 获取关闭按钮
  const closeButton = document.getElementById("J_close-button");

  // 绑定一个点击事件
  navIcon.addEventListener("click", function () {
    // 让遮罩层显示
    mask.style.display = "block";
    // 让垂直菜单显示
    mobileNav.style.display = "block";
  });

  // 给关闭按钮绑定一个点击事件
  closeButton.addEventListener("click", function () {
    // 让遮罩层隐藏
    mask.style.display = "none";
    // 让垂直菜单隐藏
    mobileNav.style.display = "none";
  });

  /* 实现二级伸缩菜单 */
  // 采用事件委托的方式
  // 首先要获取 ul 元素
  const mobileNavList = document.getElementById("J_moible-nav-list");
  // 给 ul 添加 click 点击事件
  mobileNavList.addEventListener("click", function (e) {
    // 获取触发事件的元素
    const target = e.target;
    // 判断触发事件的元素的标签名是不是 h3
    if (target.tagName.toLowerCase() !== "h3") return;

    // 如果是 h3标签，则执行后面的代码
    // 我要给 h3 标签（js对象）添加一个属性，用来记录当前菜单状态
    // flag  如果 flag 的值是 false 表示菜单是收缩的
    // 如果 flag 的值是 true 表示菜单是展开的
    // 没有属性时 target.flag 就是 undefined

    if (!target.flag) {
      // 当前菜单是收缩的，那我们就可以展开他
      // 更改菜单的状态
      target.flag = true; // 把菜单的状态改为展开
      // 实现菜单的展开效果
      // 展开的本质就是动态的计算 li 的高度
      /* 
    需要动态的计算当前 li的高度 
     收缩时 li高度 = h3 高度 + h3 的margin-bottom   =64px 
    展开时 li高度=h3 高度 + h3 的margin-bottom + dl可视区高
    */ // 获取h3的可视高（height+padding+border)
      const h3Height = target.offsetHeight;
      // 获取h3的 margin-bottom
      const h3MarginBottom = parseInt(
        window.getComputedStyle(target).marginBottom
      );
      // 还要获取二级菜单 dl的可视高
      const dlHeight = target.nextElementSibling.offsetHeight;
      // 计算当前li的高度
      const liHeight = h3Height + h3MarginBottom + dlHeight;
      // 设置当前li的高度
      target.parentNode.style.height = liHeight + "px";
    } else {
      // 当前菜单是展开的
      target.flag = false; // 把菜单的状态改为收缩

      const h3Height = target.offsetHeight;
      // 获取h3的 margin-bottom
      const h3MarginBottom = parseInt(
        window.getComputedStyle(target).marginBottom
      );
      // 计算当前li的高度
      const liHeight = h3Height + h3MarginBottom;
      // 设置当前li的高度
      target.parentNode.style.height = liHeight + "px";
    }
  });
}
```