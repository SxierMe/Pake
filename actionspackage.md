# Pake - 支持三端平台的一键网页打包桌面客户端程序

## 一、Pake简单介绍

​	Pake是一个将网页打包成桌面客户端的程序。它支持 Mac / Windows / Linux三个系统，也就是说一个网页，可以将其打包成三个系统都能安装的桌面客户端。

​	目前Pake的特性有以下几点：

- 🎐 相比传统的 Electron 套壳打包，要小将近 20 倍，5M 上下。
- 🚀 Pake 的底层使用的 Rust Tauri 框架，性能体验较 JS 框架要轻快不少，内存小很多。
- 📦 不是单纯打包，实现了快捷键的透传、沉浸式的窗口、拖动、样式改写、去广告、产品的极简风格定制。
- 👻 只是一个很简单的小玩具，用 Rust 替代之前套壳网页打包的老思路，其实 PWA 也很好。

​	其中， Pake将打包的难度分成了三个等级，不同的熟悉程度有不同的玩法：

- 小白用户：

  - 完全不懂编程，可以使用Pake提供的`常用下载包`来进行安装。目前`常用下载包`有以下应用：

    ![image-20230429192055994](https://s2.loli.net/2023/04/29/yvNAjuwzxbpP7ED.png)


- 开发用户：使用 「命令行一键打包」，对 Mac 比较友好，Windows / Linux 需折腾下 [环境配置](https://tauri.app/v1/guides/getting-started/prerequisites)。

- 折腾用户：假如你前端和 Rust 都会，那可试试下面的 「[定制开发](https://github.com/tw93/Pake/blob/master/README_CN.md#定制开发)」，可深度二次开发定制你的功能。

**官方GitHub地址是**：[点击跳转]([tw93/Pake: 🤱🏻 Turn any webpage into a desktop app with Rust. 🤱🏻 很简单的用 Rust 打包网页生成很小的桌面 App (github.com)](https://github.com/tw93/Pake))







## 二、开始Action打包

**开始打包前不要忘记给开发者点星星**



### 2.1 Fork项目

- [点击一键Fork项目](https://github.com/tw93/Pake/fork)之后，跳转到你自己的Github项目，点击`Create Fork`。

![image-20230429193137368](https://s2.loli.net/2023/04/29/Qd7JXelpVFf9yNR.png)

- Fork好之后，找到并进入`Action`

  ![image-20230429193353805](https://s2.loli.net/2023/04/29/BeEOt2oY4LjTpS9.png)

- 点击`我了解`

  ![image-20230429193500286](https://s2.loli.net/2023/04/29/aLtbBryHjMcRsxn.png)

### 2.2 开始打包

- 进入Action页面， 按照顺序进行点击。第三步的时候，需要注意的是`platform`、`URL`和`Name`三个参数

  - platform：选择你需要打包的系统。比方我是Windows，那我就选`Windows-latest`
  - URL：你想要打包的网页地址。比方说我需要把YouTube打包，那我就输入`www.youtube.com`
  - Name：应用的名称，你打包什么程序就用什么名称， 我这用`YouTube`（最好用英语）
  - ICON（可选）：可以把应用图标换成你想要的。需要注意的是不同的系统有不同的格式要求
    - MacOS 下必须为 `.icns`
    - Windows 下必须为 `.ico`
    - Linux 下必须为 `.png`
  - 其他的都是可选，默认就行，不多介绍了。 

  填写好之后，点击`Run Workflow`。

  ![image-20230429194118548](https://s2.loli.net/2023/04/29/re16nRJM9HWITja.png)

- 预计3-4秒后出现`Build App with Pake Cli`，然后静静等待进行打包。**打包时间有点长，可以抽空做点其他事情。**

  ![image-20230429195136104](https://s2.loli.net/2023/04/29/9RYOia3t6PrScdE.png)

- 当橙色小点变成小绿点之后，即为打包完成，同时点击进去。

  ![image-20230429200947373](https://s2.loli.net/2023/04/29/SNC3fe15aVgHlMc.png)

- 点进去之后，可以看到我的状态是`成功`，打包时间是`16分45秒`，打包的桌面客户端是`Windows`。我们点击箭头所指处的文件`output-windows-latest.zip`进行下载。

  ![image-20230429201404745](https://s2.loli.net/2023/04/29/qmTwQ2gDnVJAtlf.png)

  

### 2.3 安装测试

**开始安装**

- 对下载的zip压缩包文件解压后， 可以看到一个`YouTube.msi`的可执行文件，双击进行安装。

  ![image-20230429201759621](https://s2.loli.net/2023/04/29/AuT4hkPisGX3fWI.png)

- 双击进行安装， 点击`Next`,然后选择你的安装路径继续`Next`，点击install开始进行安装。

- 效果一览

  ![image-20230429202154904](https://s2.loli.net/2023/04/29/GUqtIKuFD786P5x.png)

**使用测试**

- 内存与CPU（安装后不动）

  ![](https://s2.loli.net/2023/04/29/mbsN47CU2XvH1lQ.png)

- 4K测试

  ![image-20230429202743683](https://s2.loli.net/2023/04/29/LJ8cNKqjigGd1zA.png)

## 三、Pake VS Webcatelog

### 3.1 Webcatelog简单介绍

​	Webcatelog 是一个安装在电脑上的桌面客户端， 免费账户可以使用5个网页打包服务。可以自定网页打包或是在app商城下载已经打包好的桌面客户端。 

​	所有打包的程序体积都算在一个母体程序中。 所以如果你打包了一个桌面客户端，需要卸载Webcatelog的话，你所打包的所有桌面客户端都将卸载，**无法做到独立**。 

![image-20230429224125585](https://s2.loli.net/2023/04/29/P3y7mUtoZLdx1gG.png)



###  3.2 Pake VS Webcatelog 内存对比

- 上边的YouTube是Wencatelog打包的；下边的YouTube是Pake打包的，差距非常明显。

  ![](https://s2.loli.net/2023/04/29/jvE1CZftJhDakIl.png)



### 3.3 Pake VS Webcatelog 功能对比

| 序号 |      功能      | Pake | Webcatelog |
| :--: | :------------: | :--: | :--------: |
|  1   |   占用内存低   |  √   |     ×      |
|  2   |      免费      |  √   |     ×      |
|  3   |   网页热更新   |  √   |     √      |
|  4   | 无母体程序依赖 |  √   |     ×      |
|  5   |    打包速度    |  ×   |     √      |
|  6   | Vercal.app打包 |  ×   |     √      |
|      |    后续更新    |      |            |

> 注：打包的速度会在后边越来越快，官方说是有缓存了。 





