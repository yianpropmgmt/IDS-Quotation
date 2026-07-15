# 装修点菜报价系统 — 生成 APK 安装包说明

这个文件夹是一个"可安装的离线网页应用"（PWA），已经包含生成 APK 所需的全部文件：

- index.html — 报价系统本体（跟网页版功能一摸一样）
- manifest.json — App 的名称、图标、主题色设置
- service-worker.js — 离线缓存脚本，让 App 断网也能打开
- icons/ — App 图标（192x192 / 512x512）

## 方法 A：先在自己电脑上测试（可选，非必须）

如果你想先看看效果，可以把这整个文件夹放到你自己的一个小型网页服务器上测试
（比如用 VSCode 的 Live Server 插件），用手机 Chrome 打开，右上角菜单选
"添加到主屏幕"，就会看到图标和全屏效果。如果嫌麻烦，可以跳过这步，直接进
方法 B。

## 方法 B：用 PWABuilder 直接生成 APK（推荐，最简单）

1. 打开浏览器，访问 **https://www.pwabuilder.com**
2. 因为这个 App 现在只是本地文件，还没有一个公开网址，PWABuilder 需要一个
   网址才能扫描。你有两个选择：
   - **最简单**：把这个文件夹上传到 GitHub Pages（跟你现有的报价网站部署方
     式一样），拿到网址后，粘贴到 PWABuilder 首页的输入框，点 "Start"。
   - 或者找任意免费静态网页托管（Netlify、Vercel 都可以拖拽文件夹直接发
     布），发布后把网址填进 PWABuilder。
3. PWABuilder 扫描完成后，会给出一个"打分报告"，正常这几个文件已经包含了
   它需要的 manifest 和 service worker，能直接过。
4. 页面上方选择 **"Android"** 这个选项卡，点击 **"Generate Package"**（生
   成安装包）。
5. 保持默认选项即可（除非你想改包名 Package ID，默认类似
   com.pwabuilder.xxx，也可以改成你自己的，比如 my.idsquotation.app）。
6. 点击下载，会得到一个压缩包，里面有 **.apk** 文件（还有一个 .aab，用于
   上架 Google Play 用，日常安装用 .apk 即可）。
7. 把 .apk 文件传到安卓手机上，打开安装（首次安装可能需要在手机设置里允许
   "安装未知来源应用"），装好之后就是一个独立图标的 App，断网也能用、数据
   保存在手机本地。

## 关于往后更新

以后如果报价内容或样式要改，只需要改 index.html 这一个文件，重新发布到同
一个网址，PWABuilder 那边重新生成一次 APK 即可，不需要重新配置。
