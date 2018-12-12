# How Lottie Works

## 基本概念介绍
Lottie 是利用BodyMovin 插件将AE 动画导出为带有规则的标记语言文件, 比如json, html等等. 所以首先介绍下AE动画的一些基
础概念.

### Composition

一个Composition 是一个Movie 框架, 一个动画的载体, 是layer 的container. 它有自己的时间线, 同时包含了一个或者多个layer, 每一个layer分别代表了不同的组件,
比如视频, 音频, 可以做动画的文字, 矢量图, 静止图片, 和光线等等. Composition 利用透明度的特点来决定, 控制什么时间和空间什么时候, 什么地方某一
个底层的Layer显示. 这个过程叫做Composite.

修改Layer之间透明度的可以用以下的方法:

#### Transparent Effects
可以例如如下的一些效果来实现layer 的透明效果, 最终达成控制不同layer的显示和隐藏.
* Roto Brush and Refine Edge tools in CC
* Masks (会在Android 中用到)
* Matte (会在Android中用到)
* Painting on the alpha channel (会在Android中用到)
* The Preserve Underlying Transparency layer option
* Keying effects

如果是想要整个Layer的各个区域的透明度或者般透明度都是一致的, 修改 Layer的 opacity 属性.

### Layer
Layer 是组成Composition 的元素. 没有Layer, Composition 就是一个空的Frame. 有以下集中不同的Layer:
* Video audio layer, 使用视频, 音频, 图片作为footage.
* 特殊的layer: 用来执行某些特殊的方法. null objects layer, adjustment layers.
* Solid-color layers.
* Synthetic Layer, text layers.
* PreComposition layer, 使用Composition 作为Footage的layer.

当修改一个layer的时候, 不会对它的Source Footage进行修改, 对一个layer的修改, 不会影响到其他的layers, 除非是特殊指定了某一个layer.

在Lottie Android 中共有六种Layer:  Shape, Solid, Image, Comps, Nulls, Texts.

#### Layer Property
每一个layer 都有各种的属性, 可以用来修改或者**做动画**. 一个基础的属性组是: Transform, 它包含了Position 和 Opacity 属性. 这些属性是随时间或者
空间变化的. 比如Opacity, Position. Layer 还可以添加其他的属性, 比如masks 或者 effects.

#### Blending Layers
控制两个上下叠加的Layer 的颜色如何最终混合到一起的. 这是一种可以用来控制下边的Layer如何显示的方法.

### Animation
动画随时间变化, 每一个Layer都可以做动画, 或者对Layer 的effect 做动画, 通过跟随时间修改Layer的一个或者多个的属性值. 这个跟Android 中的属性
动画类似.需要确定至少两个KeyFrame, 和时间(用来确定在动画某个时间点的某个参数的具体的值).跟属性动画一样. 然后可以使用不同的插值器(Interpolator),
修改动画的表现.

## 对比 PropertyAnimation 和 Lottie

























