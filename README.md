# TG工作室学习资源网站后台管理页面

![](https://img.shields.io/badge/webpack-3.8.1-green.svg) ![](https://img.shields.io/badge/vue.js-2.5.2-green.svg) 
![](https://img.shields.io/badge/uediter-1.4.3-green.svg)

### 项目简介
此项目为方便CTG工作室成员编辑学习分享平台的资源

### 开发者：
 前端：王智@Joe19970619
 
### 技术栈：
>**本项目前端脚手架采用Vue—cli**，**异步请求方案使用Axios**，Axios 是一个基于 promise 的 HTTP 库,可以用在浏览器和 node.js 中。**富文本编辑器采用Uediter**，UEditor是百度的一个javascript编辑器的开源项目


### 项目启动

在本地 shell 或者 git bash 里分别运行如下命令：

- git clone git@github.com:TGclub/TGproject_resource-website-admin.git
- cd TGproject_resource-website-admin
- cnpm install(或者npm install) （本地没有node的先去下载node）
- npm run dev
- 在浏览器输入 http://localhost:8086


### 代码结构介绍

```
    - build // webpack配置
    - config // 配置文件
    - dist // build之后的文件
    - mock // 用于数据模拟，方便本地调试
    - src // 源代码
        - assets // 用于存放请求的资源，如图片
        - components // 组件
        - App.vue // 主页面
        - main.js // 入口文件
    - .babelrc // babel配置文件
    - editerconfig // 编辑器风格统一配置文件
    - .gitignore // git忽略文件
    - .postcssrc.js // postcss的配置文件
    - README.md // readme说明
    - index.html // 主页面
    - package.json // 依赖文档
    
```
## 编辑风格使用说明如下
## 1.在编辑器里文本应该如下所示
![123](http://upload-images.jianshu.io/upload_images/2768522-f86edfb8313558ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>注意：所有文字为默认样式，不得设置字号，粗细等，之所以不允许自己设定样式，是因为会引发浏览器兼容问题，**还有，请不要进行多余的折行**

### **知识图谱的图应如下方式引入**
![123](http://upload-images.jianshu.io/upload_images/2768522-431e781e57bf61a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>以在线链接方式导入即可

### **网站资源部分的链接应如下方式引入**
![123](http://upload-images.jianshu.io/upload_images/2768522-56aca1b572d2827d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>如图，将要显示的内容放为链接的的文本内容处，链接添至链接处即可，**多个链接之间不必打空格，样式我在前端中会处理**

### **学习资料部分的链接应如下方式引入**
![123](http://upload-images.jianshu.io/upload_images/2768522-8402822b417921c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>同上，如图，将所有文本放在链接的的文本内容处，文本只需放置密码即可，链接添至链接处即可，**同样，多个链接之间不必打空格**

## 2.最终请在HTML格式中检查下是否基本如下所示
![123](http://upload-images.jianshu.io/upload_images/2768522-c4a3cae541691dab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>请尽量删除多余的br标签,我在前台会对br标签进行处理，但还是麻烦再编辑时尽量避免过多的br标签，按照沙砼同学所发的word格式，**一共会产生6个p标签**，请检查仔细

## 只要按照以上格式无误，最终在页面呈现效果如下
![123](http://upload-images.jianshu.io/upload_images/2768522-e93756783d0191e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![123](http://upload-images.jianshu.io/upload_images/2768522-8c8614a4b89200db.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


