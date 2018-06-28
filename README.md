# 谷歌浏览器开发者工具

## 基础功能篇

### 1. elements

在elements中主要分为两大块：

A：HTML结构面板 

B：操作dom样式、结构、事件的显示面板 

（1）点击箭头选中一个元素，可以在HTML面板中定位到该元素，并且可以在右侧styles面板中查看和编辑该元素的样式，编辑时，效果可以实时更新，这对于前端工程师解决样式问题是个大大的福利，在HTML面板中ctrl+F，可以对html中的内容进行搜索。

![](https://github.com/FloweringVivian/Google-developer-tools/blob/master/images/elements-1.png)



（2）在右侧Computed面板中，可以查看对应元素的盒图和该元素上最终生效的样式（包含继承父级元素的样式和自己的样式）

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-2.png)



（3）Event Listeners面板可以查看对应元素绑定的事件（旧版本谷歌浏览器不太好用，更换选取元素时该面板不会实时更新，只有重新打开审查元素才可以，新版本谷歌浏览器已解决这个问题，可以实时更新）

click：是事件名称 

handler里面包含事件的回调主体内容 

useCapture表示该事件是否向上冒泡

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-3.png)



还有一个方法，如果想要找到一个元素绑定的事件，我喜欢用google浏览器的search all files，搜索元素的id或class，从而找到该元素在js中绑定的事件，如下图：

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-4.png)



（4）在HTML面板中选中一个元素，鼠标右键点击，会看到一个弹窗，里面有若干选项：

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-5.png)

* Add attribute : 为该元素添加属性 

* Edit attribute：修改该元素的属性 

* Edit as HTML :  编辑该元素（你可以重写它的整个content）甚至修改它的标签名称 

* :active / :hover / :focus / :visited : 点击这四项 元素被激活 / 鼠标滑过 / 获得焦点 / 链接点击之后 四个状态下元素的样式可以在右侧styles中显示

* Break on：为该元素添加dom操作事件监听。包含三个选项（树结构改变、属性改变、节点移除）。这个选项的作用是帮助我们监控和定位操作元素的代码 

  针对Break on的示例如下：

  ![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-6.png)
  

勾选Break on -> Node removal，在B界面切换到DOM Breakpoints 选项，可以看到有注册信息。然后我们点击click me按钮触发删除div3的事件，可以看到浏览器自动为我们定位删除该元素的代码部分，并且停止执行js代码。 



### 2. **Network** 

Network是一个监控当前网页所有的http请求的面版，它主体部分展示的是每个http请求，每个字段表示着该请求的不同属性和状态 。

单击面板中的任意一条http信息，会在底部弹出一个新的面板，其中记录了该条http请求的详细参数：

header（表头信息、返回信息、请求基本状态）

Preview（返回的格式化文本信息）

response（返回的原始信息）

Cookies（该请求带的cookies）

Timing（请求时间变化） 

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-8.png)



### 3. **Application** 

Application部分较简单，其中Frames主要向我们展示了本界面所加载的资源列表。还可以看到cookie和local storage 、session storage 等本地存储信息，在这里，我们可以自由地修改、增加、删除本地存储 。

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-9.png)



## 进阶篇

### 1. Sources：谷歌浏览器开发者工具中最有用的面板

Sources面板几乎是前端开发工程师最常用到的功能面板，也是在我看来决解一般问题的主要功能面板。通常只要是开发遇到了js报错或者其他代码问题，在审视一遍自己的代码而一无所获之后，就会打开Sources进行js断点调试，而它也几乎能解决我80%的代码问题。 

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-10.png)

左侧双击某个js，在右侧的行号上点击进行打断点，上图中的1~6分别代表：

1、停止当前断点调试

2、不跳入函数中去，继续执行下一行代码（F10）

3、跳入函数中去（F11）

4、从执行的函数中跳出

5、禁用所有的断点，不做任何调试

6、程序运行时遇到异常时是否中断的开关

（以设置云控制锁pin码为例进行演示）



当你的项目已经线上，出现了一个bug，你修复了之后无法看到它真正在线上的效果，那么你可以在打开线上的项目，直接在浏览器中修改代码然后看到效果。这样的效果往往是最直接的，这种方法也能帮你省去频繁验证发布的麻烦，毕竟身为前端码农的你也一定会听到过后台（通常情况下是后台发布）大哥的抱怨：“XXX，测试通过了没，不要出现了哈，发布一次很麻烦的！”。而在谷歌浏览器打断点的文件中直接修改，你就可以验证你的代码在线上是否可行。 

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-11.png)

即使在断点时，你也可以编辑代码，按ctrl+S保存之后，你会看到断点区域的背景由白色变为浅色，而断点会重新开始执行 ，此时你就可以验证改的bug是否生效。



### 2. Audits

Audits面板会针对目前网页提出若干条优化的建议，这些建议分为两大类，一类是网络加载性能，另一类是界面性能。首先打开它的主界面。 

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-12.png)



**Audits**面板的网络优化建议参照的是雅虎前端工程师的十四条黄金建议，详情请[点击这里](http://www.360doc.com/content/16/0426/10/30281360_553888492.shtml)。

（1）减少HTTP请求次数

（2）使用CDN(Content Delivery Network，内容分发网络) 

（3）增加Expires Header 

（4）压缩页面元素 

（5）把样式表放在头上 

（6）把脚本文件放在底部 

（7）避免CSS表达式

（8）把JavaScript和CSS放到外部文件中 

（9）减少DNS查询次数 

（10）最小化JavaScript代码 

（11）避免重定向 

（12）删除重复的脚本文件 

（13）配置ETags 

（14）缓存Ajax



点击run，进行测试（以开发者网站和计费中心充值进行演示）

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-13.jpg)



### 3. **Console** 

**Console**面版可以输出你自己代码 ，功能非常强大，详细讲解请 [点击这里](http://www.cnblogs.com/constantince/p/4624241.html ) 查看一位大神的文章。

（以获取输入密码、Base64加密解密、on/off的checked属性为例进行讲解）



### 4. 移动开发模式

点击elements左侧小手机的图标，即可进入移动开发模式，并不能完全模拟出手机的真实情况（比如手机会弹出软键盘，引起兼容问题）

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-14.png)



## 性能篇

一个网站的性能主要关乎两项，一是加载性能、二是执行性能。第一项可以利用**Network**来分析， 第二项可以利用**Timeline**来分析。

加载性能分析：

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-15.png)



**Request sent（发送请求）**：发送HTTP请求的时间（从第一个bit到最后一个bit） 　　

**Waiting（等待响应）**：通常是耗费时间最长的。从发送请求到收到响应之间的空隙，会受到线路、服务器距离等因素的影响。 　　 

**Content Download（下载）**：下载HTTP响应的时间（包含头部和响应体） 　　



执行性能分析（有待深入研究）：

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-16.png)



## 插件篇

#### 1. **(FeHelper)WEB前端助手** 

![](https://github.com/FloweringVivian/addLicensePlate/blob/master/images/elements-17.png)



#### 2. **Vue.js devtools：调试vue** 



#### 3. **React Developer Tools：调试react** 


