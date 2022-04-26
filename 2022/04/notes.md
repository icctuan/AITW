## 4.25 - 5.1

### 1.Git - cherryPick

### 2.React 父子组件传值

### 3.TS - interface 和 type 的区别

### 4.Grid 布局

### 5.图片自适应布局

> 示例：examples/img.html

用在 img 上：

#### _object-fit_

```
属性：{
1）fill：默认，不保证保持原有的比例，内容拉伸填充整个内容容器。
2）contain：保持原有尺寸比例。内容被缩放。
3）cover：保持原有尺寸比例。但部分内容可能被剪切。
4）none：保留原有元素内容的长度和宽度，也就是说内容不会被重置。
5）scale-down：保持原有尺寸比例。内容的尺寸与 none 或 contain 中的一个相同，取决于它们两个之间谁得到的对象尺寸会更小一些。
6）initial：设置为默认值。
7）inherit：从该元素的父元素继承属性。
}
```

用在背景图上：

#### _background_

bg-color bg-image position/bg-size bg-repeat bg-origin bg-clip bg-attachment initial|inherit;

```
background-color: 指定要使用的背景颜色

background-position: 指定背景图像的位置

background-size:	指定背景图片的大小
  1.cover：把背景拉伸，适应整个盒子，可能导致有一部分图片显示不全；
  2.contain：拉伸背景，只要有一边适应了盒子就马上停止，会导致盒子一部分没背景；
  如果都设置100%，会让背景完全适应盒子。一个值代表宽，高。如果高是auto，则宽等比例缩放。

background-repeat:	指定如何重复背景图像

background-origin:	指定背景图像的定位区域，背景位置
  1.border-box：把背景延伸至边框；
  2.padding-box：把背景延伸至padding位置；
  3.content-box：背景只在内容里边。

background-clip:	指定背景图像的绘画区,背景剪切区域
  1.border-box：把背景裁剪至边框区域；
  2.padding-box：裁剪至内边距区域；
  3.content-box：裁剪至内容区域。

background-attachment:	设置背景图像是否固定或者随着页面的其余部分滚动

background-image:	指定要使用的一个或多个背景图像
```
