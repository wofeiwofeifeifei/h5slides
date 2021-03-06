# H5Slides

`H5Slides`希望通过HTML5的技术，成为用户编辑、播放、控制幻灯片这一系列行为的全套方案的提供者。幻灯演示将会变得更自如，更轻便，更开放，更易于分享。

## 特点

1. 它是HTML5的！
2. 我们不需要臃肿的Powerpoint也可以自由的制作和演示幻灯片
3. 我们可以自由的在各种设备上进行幻灯演示
4. 我们可以自由扩展幻灯片的制作工具和播放环境
5. 它可以很自由很方便的传播

### 它不是……

* 它不是个重量级选手
* 它不是个全能型选手
* 它不是PPT，而是`H5Slides`！

## 运行方式

### 运行环境

`H5Slides`支持所有的webkit内核浏览器(safari/maxthon/chrome)，这包括Safari for iPad版本的触摸操作。在支持`FileSystemAPI`的新版webkit内核下(chrome 17+/maxthon 3.3.7+)，还允许用户上传图片，并设置为幻灯片背景等。

我们对于非webkit内核的浏览器也非常尊重，我们接下来会有一些[兼容其他内核](#兼容更多的环境)的打算。感兴趣的朋友可以移步到项目进展和规划的章节了解情况或参与其中。

目前，在非webkit内核浏览器下，`H5Slides`会给用户一个较为友好的提示界面，推荐用户通过webkit内核浏览器进行使用。

### 运行步骤

* 用webkit内核浏览器打开源代码中的`index.html`即可运行；
* 在新打开的界面中，我们可以自由编辑幻灯片的内容和样式；
* 点击右上角的“播放”按钮，可以进入播放器模式，播放我们之前编辑好的幻灯片；
* 如果想重新编写一个全新的幻灯片，可以点击右上角的“重做”按钮。

----

## 我们的计划

`H5Slides`还是个很初级的WebApp，我们希望大家可以一同参与其中，共同打造我们自己的幻灯演示平台！欢迎为我们push代码，如果希望更深入的交流，可以随时与我们[取得联系](#我们的联系方式)。

我们看得到的可完善的空间(2012.04.23更新)会放在下面；而同时，这里有一些多多益善的事情可以让大家都参与进来：

### 幻灯素材

* 制作更多皮肤 —— 我们会提供[皮肤开发文档](#皮肤开发文档)
* 制作更多动画 —— 我们会提供[动画开发文档](#动画开发文档)
* 更多插件 *1

### 数据处理

* 数据结构的扩展 —— 我们会提供[数据格式说明文档](#数据格式说明文档)
* 附件管理(如图片等)
* 数据导入导出

### 完善编辑器功能

* 美化编辑器的界面
* 调整布局位置
* 修改字体
* 选择动画
* 幻灯片排序
* 撤销&恢复
* 配置插件 *1
* 插入widget *2
* 设置页面内的动画 *3

### widget机制 *2

* 富文本编辑器
* 图片
* 流程图
* 报表
* 视频
* 地图
* 问卷

### 兼容更多的环境

* 兼容平板
* 兼容其它浏览器


#### 注

1. 插件是指播放器在播放幻灯演示时的附加功能(如允许演示者在幻灯片上涂鸦等)，插件系统目前还在设计之中
2. widget是指可以插入幻灯片中的多媒体内容或复杂内容，以widget的形式插入其中，widget系统目前还在设计之中
3. 页面内的动画是指幻灯片内容的分步骤呈现的效果，目前还在设计之中

#### 我们的联系方式

我们的github页面：[https://github.com/Jinjiang/h5slides](https://github.com/Jinjiang/h5slides)  
我们的邮箱：[h5slides@gmail.com](mailto:h5slides@gmail.com)  
我的个人微博：[@勾三股四](http://weibo.com/mx006)  

----

## 皮肤开发文档

皮肤是基于幻灯片布局和幻灯片内部元素的样式和尺寸的设计。每款皮肤应该拥有一个唯一的名称，在展示时，幻灯片的根结点会被赋予`[data-design="*"]`特性。比如`[data-design="blue-summer"]`。

### 皮肤文件格式

每一款皮肤都是由一个css文件作为起点，存放在`/css/theme/`目录下的和皮肤名称同名的css文件中。该css文件的内容应该是一系列主题特性、布局特性、内部元素特性及其样式的集合。比如：

    [data-design="blue-summer"] [data-layout="title"] [data-item="content"] {
        color: blue;
        width: 480px;
    }
    [data-design="blue-summer"] [data-layout="subtitle"] [data-item="content"] {
        color: navy;
        width: 420px;
    }
    ......

其中，布局是基于`[data-layout="*"]`的，默认的布局情况一共有5个：

* `title`: 大标题页面
* `subtitle`: 小标题页面
* `normal`: 正文页面
* `double`: 两列正文页面
* `double-subtitle`: 两列正文且每列正文带子标题的页面

内部元素是基于`[data-item="*"]`的，默认的内部元素一共有5个：

* `title`: 标题元素
* `subtitle`: 第一子标题元素
* `subtitle2`: 第二子标题元素
* `content`: 正文元素
* `content2`: 第二正文元素

幻灯片布局和内部元素的对应关系如下：

* 每个大标题页面都包含一个标题元素和一个正文元素
* 每个小标题页面都包含一个标题元素和一个正文元素
* 每个正文页面都包含一个标题元素和一个正文元素
* 每个两列正文页面都包含一个标题元素和两个正文元素(正文元素和第二正文元素)
* 每个两列正文带子标题的页面都包含一个标题元素、两个子标题元素(第一子标题元素和第二子标题元素)和两个正文元素(正文元素和第二正文元素)

默认的主题样式可参考`/css/theme.css`

### 使用定义好的皮肤

打开`/data/themes.js`，加入一行数据，比如：`{"key": "blue-summer", "title": "蓝色夏天"}`，同时，在`/css/theme/`下新建一个该皮肤的同名目录，并放入`logo.png`作为皮肤展示时的缩略图。然后在编辑器左侧边栏的“主题”面板下会看到这个主题的缩略图。点击该缩略图，即可应用主题。

----

## 动画开发文档

### 播放器的dom结构

幻灯片在播放时的根结点是`#player`，每张幻灯片是一个`section`结点。默认情况下幻灯片都是隐藏起来的(`display: none;`)，只有正在播放的那张幻灯片是显示出来的(`display: block;`)。

### 动画的实现原理

由于`display`的属性值在`none`和`block`之间切换是没有动画效果支持的，我们做了一点改进：把当前幻灯片、前一张幻灯片和后一张幻灯片，分别赋予特殊的className：`.current`、`.prev`、`.next`。他们三个的`display`属性值均为`block`，同时`.prev`和`.next`的`opacity`属性值为`0`，`.current`的`opacity`属性值为`1`。这样幻灯片的切换就会有渐变效果。基本的css样式如下：

    #player section {
        display: none;
        transition: all 0.3s ease-out;
    }
    #player section.current {
        display: block;
        opacity: 1;
    }
    #player section.next,
    #player section.prev {
        display: block;
        opacity: 0;
    }

### 动画文件格式

我们可以在此基础上，通过css代码加入更酷炫的幻灯片切换动画。和皮肤开发相同的，我们需要为每种动画效果起一个名字。比如：`horizontal`。然后，我们可以在`/css/transition/`目录下创建一个同名的css文件。

这个css文件中，我们为幻灯片中的`section`元素增加一个`data-transition`属性：`section[data-transition="transition_horizontal"]`(注意，属性值前需要加入`transition_`前缀)。然后将`.current`、`.prev`、`.next`下的不同样式写入即可。比如：

    [data-transition="transition_horizontal"].next {
        left: 450px;
    }
    [data-transition="transition_horizontal"].current {
        left: 0;
    }
    [data-transition="transition_horizontal"].prev {
        left: -450px;
    }

### 使用定义好的动画

目前使用动画的方法是：打开`/js/app.js`，把其中的变量`defaultTransition`改为带`transition_`前缀的动画名即可。比如：

    var defaultTransition = 'transition_horizontal';

再使用播放器，就可以看到效果了。

----

## 文件/目录结构说明

* `/css/`: 基本样式文件
* `/css/theme/`: 主题样式集合，每个主题是一个同名css文件，可以伴随同名文件夹包含更多内容
* `/css/transition/`: 切换动画集合，每个动画是一个同名css文件
* `/js/`: 脚本文件
* `/js/lib/`: 基础函数库
* `/js/ui/`: 界面相关的脚本
* `/data/`: 脚本数据，包括可用布局列表、可选主题列表、初始化数据信息等

----

## 数据格式说明文档

默认数据保存在`/data/default.js`中，变量名为`defaultData`。

    var defaultData = {
        "theme": "blank",
        "slides": [
            {
                "layout": "title",
                "content": {
                    "title": "幻灯片标题",
                    "content": "你的名字"
                }
            },
            {
                "layout": "normal",
                "content": {
                    "title": "正文标题",
                    "content": "正文内容\n是可以多行显示的"
                }
            },
            {
                "layout": "subtitle",
                "content": {
                    "title": "THE END",
                    "content": "谢谢大家"
                }
            }
        ]
    };

### 字段解释

#### `theme`

默认主题名称

#### `slides`

以数组形式存放所有幻灯片的详细内容

#### `slides[i].layout`

某张幻灯片的布局类型，有效的值有：`title`、`subtitle`、`normal`、`double`、`double-subtitle`

#### `slides[i].content[key]`

某张幻灯片的所有内部元素的文字内容，有效的key值有：`title`、`subtitle`、`subtitle2`、`content`、`content2`

#### `slides[i].position[key][cssName]`

某张幻灯片的自定义元素尺寸和位置，有效的key值同上，有效的cssName值有：`left`、`top`、`width`、`height`。

目前我们的编辑器暂不支持编辑尺寸和位置，使用时可以通过直接修改`defaultData`的值来应用这一规则。

#### `slides[i].style[key][cssName]`

某张幻灯片的自定义元素尺寸和位置，有效的key值在同上的基础上外加一个`slide`，表示该幻灯片整体的样式，有效的cssName值除了上一条提到的属性值外，还不支持：`right`、`bottom`；另外支持形如`-ppt-*`的属性值，以备扩展。

目前已有的扩展只有一个，就是`-ppt-size`，用来控制文字大小，可选的`-ppt-size`属性值有：`small`、`normal`、`large`。

目前我们的编辑器暂支持编辑`color`、`-ppt-size`和`slide`下的`background-image`这几个css属性。若想使用其它css属性，可以通过直接修改`defaultData`的值来应用这一规则。

