# 简历

来龙去脉: 作为一个iOS开发者,从接触swift一直深受喵神的影响, 看大神的博客做的真是漂亮, 之前用了喵神的博客模板, 现在我也再次参照大神的简历弄一份. 

该项目采用的是[Hugo](https://gohugo.io/) 搭建静态网站.
简单使用, 我也就不啰嗦了.

## 教程

确保安装最新的 `node`, `npm` and [Hugo](https://gohugo.io/). 
在`OSX`安装, 运行命令:

```bash
brew install hugo
```

如果不使用 `OSX` or 或者 `homebrew`, 则使用下面的教程安装`hugo`:

http://gohugo.io/overview/installing/

下一步,克隆本项目, 运行命令:

```bash
npm install
npm start
```

然后访问地址: http://localhost:3000/ - 浏览器将自动加载CSS,并在样式表或者内容变更时,刷新页面.

使用命令:

```bash
npm run build
```
将输出静态资源到`/dist`文件夹

## 静态网站结构

```
|--site                // 这里的所有文件都会被hugo构建
|  |--content          // 页面
|  |--data             // YAML 数据文件
|  |--layouts          // 模板的布局文件
|  |  |--partials      // live
|  |  |--index.html    // 首页
|  |--static           // 将发布在`public`目录
|--src                 // 图片资源
|  |--css              // 位于该目录的根路径下的CSS文件将会生成在/css/路径下
|  |--js               // app.js 会被babel编译到该路径下 /app.js
```

## 基本内存

[更过Hugo模板](https://gohugo.io/templates/overview/)

[常用功能介绍](https://gohugo.io/templates/functions/)


发布目录变更

* 图片资源  `site/static`

* 网站图标  `site/static/favicon.ico` -> `/favicon.ico`
 
* js目录  `src/js/app.js` ->  `/dist/app.js`

* CSS文件 `src/css/` -> `/dist/css/{filename}.css`

## 部署到 netlify

- netlify上登录Github.
- [Netlify上创建新的站点](https://app.netlify.com/start)并关联Github上的本项目

之后netlify会在你推送变更时,自动构建部署你的站点了 


## 问题

#### babel/register 问题

```
Failed to load external module @babel/register
Requiring external module babel-register
```

[解决方法](https://github.com/gulpjs/gulp/issues/1631)

```
Not an issue, as it states on the next line down,
 it required babel-core/register. 
 Babel now suggests you use a module called babel-register so we try that first with the fallback. 
 Please read your entire log before creating an issue.
```

#### Cannot GET / 问题

空白页面 只显示 `Cannot GET /` , 原因是 `onevcat`项目中的依赖主题是另一个仓库, 所以我直接下载下来后,放到对应的`theme`目录下就好了

#### netlify 部署问题

描述
```
Current theme does not support Hugo version 0.17. Minimum version required is 0.18
```

[解决方法](https://discourse.gohugo.io/t/solved-netlify-deployment-errors-yet-nothing-errors-on-localhost/5895)

[netlify官方设置环境变量](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/)

```
context.production.environment]

  HUGO_VERSION = "0.18"
  HUGO_ENV = "production"
  HUGO_ENABLEGITINFO = "true"

[context.deploy-preview.environment]
 HUGO_VERSION = "0.18"
```

只要设置合适的`HUGO_VERSION`版本即可


