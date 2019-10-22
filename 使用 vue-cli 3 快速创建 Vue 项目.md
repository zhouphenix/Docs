# [使用 vue-cli 3 快速创建 Vue 项目](https://segmentfault.com/a/1190000014627083)





为了便于 Vue 项目的管理， Vue 团队官方开发了 [vue-cli](https://github.com/vuejs/vue-cli) 工具。

本文将带您使用 vue-cli 快速创建一个 Vue 项目。

# 本地安装 vue-cli

使用 npm 全局安装 vue-cli ：

```
npm i -g @vue/cli
```

yarn 安装

```
yarn global add @vue/cli
yarn global add @vue/cli-init
```



# 创建项目

执行：

```
vue create my-project
```

会弹出如下界面：

![选择套餐](https://segmentfault.com/img/remote/1460000014627088)

此处有两个选择：

- `default (babel, eslint)` 默认套餐，提供 [babel](https://babeljs.io/) 和 [eslint](https://eslint.org/) 支持。
  * babel: es6 转换es5     *  eslint: 检查代码风格
- `Manually select features` 自己去选择需要的功能，提供更多的特性选择。比如如果想要支持 TypeScript ，就应该选择这一项。

可以使用`上下方向键`来切换选项。如果只需要 babel 和 eslint 支持，那么选择第一项，就完事了，静静等待 vue 初始化项目。

如果想要更多的支持，就选择第二项：切换到第二项，按下 enter 键选中，弹出如下界面：

![选择特性支持](https://segmentfault.com/img/remote/1460000014627089)

vue-cli 内置支持了8个功能特性，可以多选：使用方向键在特性选项之间切换，使用空格键选中当前特性，使用 a 键切换选择所有，使用 i 键翻转（反选）选项。

对于每一项的功能，此处做个简单描述：

- `TypeScript` 支持使用 TypeScript 书写源码（大型的框架用到）。
- `Progressive Web App (PWA) Support` [PWA](https://developers.google.com/web/progressive-web-apps/) 支持（缓存作用）。
- `Router` 支持 [vue-router](https://router.vuejs.org/zh-cn/) （路由）。
- `Vuex` 支持 [vuex](https://vuex.vuejs.org/zh-cn/intro.html) （管理多种状态）。
- `CSS Pre-processors` 支持 CSS 预处理器。
- `Linter / Formatter` 支持代码风格检查和格式化。
- `Unit Testing` 支持单元测试。
- `E2E Testing` 支持 E2E 测试。

那么基于开发常见的项目，同时兼顾项目健壮性的原则，本次选择如下特性支持：

![特性选项](https://segmentfault.com/img/remote/1460000014627090)

按下 enter 键确认选择，进入下一步：

![image.png](https://segmentfault.com/img/remote/1460000014627091)

这里是让选择在开发 Vue 组件时，要不要使用 class 风格的写法。为了更方便地使用 TypeScript ，此处选择 Y ：

![使用 class 风格的 Vue 组件开发方式](https://segmentfault.com/img/remote/1460000014627092)

按 enter 键，进入下一步：

![image.png](https://segmentfault.com/img/remote/1460000014627093)

这个选项的意思是要不要使用 babel 工具自动为转换后的 TypeScript 代码注入 polyfiills 。如果实在搞不清楚具体是什么意思，可以先不用管，直接选择 Y ，进入下一步：

![选择 CSS 预处理器](https://segmentfault.com/img/remote/1460000014627094)

这里就是说我们在项目里面需要支持何种动态样式语言，此处提供了三个选项：

- [SCSS/SASS](https://sass-lang.com/)
- [LESS](http://lesscss.org/)
- [Stylus](http://stylus-lang.com/)

此处选择 LESS ，进入下一步：

![单测工具](https://segmentfault.com/img/remote/1460000014627095)

选择单元测试工具，直接选择现在比较火的 Jest ，进入下一步：

![配置文件位置](https://segmentfault.com/img/remote/1460000014627096)

这一步就是要选择配置文件的位置了。对于 Babel 、 PostCSS 等，都可以有自己的配置文件： .babelrc 、 .postcssrc 等等，同时也可以把配置信息放在 package.json 里面。此处出于对编辑器（ Visual Studio Code /IDEA）的友好支持（编辑器一般默认会在项目根目录下寻找配置文件），选择把配置文件放在外面，选择 `In dedicated config files` ，进入下一步：

![presets](https://segmentfault.com/img/remote/1460000014627097)

这个就是问要不要把当前的这一系列选项配置保存起来，方便下一次创建项目时复用。对于 MAC ，保存的配置信息会放在 ~/.vuerc 里面。

我这里就选择 n 了，然后进入下一步：

![registry](https://segmentfault.com/img/remote/1460000014627098)

这里是选择 npm registry ，在中国的话，就直接使用默认的淘宝镜像就行了。

选完之后， vue-cli 就根据前面选择的内容，开始初始化项目了。

# 启动项目

初始完之后，进入到项目根目录：

```
cd my-project
```

启动项目：

```
npm run serve
```

or 

```
yarn serve
```

稍等一会儿，可以看到自动在浏览器中打开了如下界面：

![界面](https://segmentfault.com/img/remote/1460000014627099)

# 打包上线

在开发完项目之后，就应该打包上线了。 vue-cli 也提供了打包的命令，在项目根目录下执行：

```
npm run build
```

执行完之后，可以看到在项目根目录下多出了一个 dist 目录，该目录下就是打包好的所有静态资源，直接部署到静态资源服务器就好了。

实际上，在部署的时候要注意，假设静态服务器的域名是 `http://static.baidu.com` ，那么对应到访问 `<项目根目录>/dist/index.html` 的 URL 一定要是 `http://static.baidu.com/index.html` ，其他的静态资源以此类推。

# 单元测试

执行：

```
npm run test
```