# vertical-align

## 1. vertical-align 属性值概览

vertical-align 仅对行内元素(inline-block、inline)生效，块元素无效，他是确定子元素的基线相对于父元素基线的位置（垂直方向上的对齐方式），其属性值有：

1. baseline
2. top
3. bottom
4. text-top
5. text-bottom
6. middle
7. sub
8. super
9. 数字

## 2. 准备

### 2.1 字体度量

![字体度量.png](https://upload-images.jianshu.io/upload_images/10053029-dbfc2eebc583bf16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

首先，我们先了解一下字体度量，如上图所示。图中小写字母 `x` 的底部为 baseline, `x` 的高度为 x-height，ascender与大写字母的顶部有一定的间距，descender与小写字母 `p`, `y` 的底部对齐，这些设置与字体的设置有关，具体的需要去了解字体是怎么做出来的，理解 vertical-align 的各个属性的基础是需要知道这些线的位置。

### 2.2 line-box

每一行称为一条Line Box，它又是由这一行的许多inline-box组成，它的高度可以直接由line-height决定，line boxes的高度垂直堆叠形成了containing box的高度，就是我们见到的div或是p标签之类的高度了。

## 3. vertical-align 各个属性的表现一览

下图中第一排为文字内容的表现，第二排为图片的表现，如果这个图让你一眼就看明白了各个属性的具体表现，那么后续的内容均可忽略。黑色的外框是父元素内容区域的边界，因为没有设置 margin 和 padding，这个边界也是line-box的边界。

下图中各个颜色的线的意义（从上到下数）：

* 蓝色线（第一条）- ascender
* 绿色线（第二条）- x-height
* 红色线（第三条）- middle
* 橙色线（第四条）- baseline
* 灰色线（第五条）- descender

![vertical-align 各个属性的表现一览.png](https://upload-images.jianshu.io/upload_images/10053029-9e8f292e4b142423.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 4. vertical-align 各个属性详述

在父元素中写入 `Xxjpf` 作为参考，并在此基础上画出5条参考线，父元素的 baseline 是 `x` 的底部的线条

### 4.1 baseline

***对齐位置：子元素的 baseline 与父元素 baseline 对齐，即子元素中 `x` 的底部与父元素中 `x` 的底部对齐，图片元素的 baseline 以及有宽度和高度的空盒子的baseline均为盒子底部。***

如图：

![baseline.png](https://upload-images.jianshu.io/upload_images/10053029-9ff161a9659d5ba1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-baseline.png](https://upload-images.jianshu.io/upload_images/10053029-c5d52ed24aeac1dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.2 sub

***对齐位置：子元素的 baseline(字母`x` 的底部)与父元素文字的 descender （灰线）对齐***

如图：

![sub.png](https://upload-images.jianshu.io/upload_images/10053029-8512ebe653097791.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-sub.png](https://upload-images.jianshu.io/upload_images/10053029-0638be285bd97b0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.3 super

***对齐位置：子元素的 baseline(字母`x` 的底部)与父元素文字的 x-height （绿线）对齐***

如图：

![super.png](https://upload-images.jianshu.io/upload_images/10053029-103988c09c668ac3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-super.png](https://upload-images.jianshu.io/upload_images/10053029-9f86a81567075147.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.4 top

***对齐位置：子元素盒模型的顶部，与 `line-box` 的顶部对齐。***

如图：

![top.png](https://upload-images.jianshu.io/upload_images/10053029-efa7ebee5606e209.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-top.png](https://upload-images.jianshu.io/upload_images/10053029-c38f778df04705de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.5 middle

***对齐位置：子元素盒模型的中线位置与父元素 基线(字母`x` 的底部)+ 半个x的高度的位置（红线）对齐***

图例中，为了方便查看，我们在子元素的中间画了一条白色的线，可以看到这条白线是与父元素穿过 `x` 中心的红线对齐。图片上的黑色的线就是图片的中间位置（是在ps上自己画上去的），也可以看到该黑线与穿过 `x` 中心的红线对齐。同时也可以看出 middle 与 baseline 的差别，文字内容的差距比较小，但图片可以明显看出是不一样的。如图：

![middle.png](https://upload-images.jianshu.io/upload_images/10053029-425201ac46301fe0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-middle.png](https://upload-images.jianshu.io/upload_images/10053029-89315f11204cb967.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.6 bottom

***对齐位置：子元素盒模型的底部，与 `line-box` 的底部对齐***

如图：

![bottom.png](https://upload-images.jianshu.io/upload_images/10053029-3ba9436cefed886f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-bottom.png](https://upload-images.jianshu.io/upload_images/10053029-47baa23bf7b1781a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.7 text-top

***对齐位置：子元素盒模型的的顶部与父元素字体的 ascender 线（蓝线）对齐***

如图：

![text-top.png](https://upload-images.jianshu.io/upload_images/10053029-a3e8a49c05f62f6f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-text-top.png](https://upload-images.jianshu.io/upload_images/10053029-7e438b85ec3d7ea7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.8 text-bottom

***对齐位置：子元素盒模型的的顶部与父元素字体的 descender 线（灰线）对齐***

如图：

![text-bottom](https://upload-images.jianshu.io/upload_images/10053029-99fc6d813acc5599.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片-text-botton.png](https://upload-images.jianshu.io/upload_images/10053029-0dcefcb0011bed5f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.9 数字

***对齐位置：以 baseline 为中心线上下移动指定像素量，正数为向上移动，负数为向下移动***

子元素 baseline 与父元素 baseline 对齐的前提下，正数（eg：2px）代表相对于baseline 位置上移指定的像素，负数（-2px）代表相对于 baseline位置 下移指定的像素

## 总结

vertical-align 只对行内元素生效，

有些属性需要找准子元素的基线，如：baseline, sub, super

还有一些属性需要确认子元素的盒模型的范围，如：top, middle, bottom, text-top, text-bottom

| 属性值      | 对齐位置                                                               |
| ----------- | ---------------------------------------------------------------------- |
| baseline    | 子元素的 baseline 与父元素 baseline 对齐                               |
| sub         | 子元素的 baseline 与父元素 x-heignt (绿线对齐)                         |
| super       | 子元素的 baseline 与父元素 descender（灰线）对齐                       |
| top         | 子元素盒模型顶部与父元素 line-box 顶部对齐                             |
| middle      | 子元素盒模型的中线与父元素 baseline + 半个 `x` 的高度位置（红线）对齐  |
| bottom      | 子元素盒模型底部与父元素 line-box 底部对齐                             |
| text-top    | 子元素盒模型的顶部与父元素 ascender 线（蓝线）对齐                     |
| text-bottom | 子元素盒模型的底部与父元素 descender 线（灰线）对齐                    |
| 数字        | 以 baseline 为中心线上下移动指定像素量，正数为向上移动，负数为向下移动 |

## 思考

如果子元素的内容有换行，如何确定baseline？
