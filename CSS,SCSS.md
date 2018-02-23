### CSS, SCSS
#### 缩进
* 使用soft tab（2个空格）。
```
.element {
  position: absolute;
  top: 10px;
  left: 10px;

  border-radius: 10px;
  width: 50px;
  height: 50px;
}
```
***
#### 分号
* 每个属性声明末尾都要加分号。
```
.element {
  width: 20px;
  height: 20px;

  background-color: red;
}
```
***
#### 空格
* 以下几种情况不需要空格：

1、属性名后
2、多个规则的分隔符','前
3、!important '!'后
4、属性值中'('后和')'前
5、行末不要有多余的空格
* 以下几种情况需要空格：

1、属性值前
2、选择器'>', '+', '~'前后
3、'{'前
4、!important '!'前
5、@else 前后
5、属性值中的','后
5、注释'/*'后和'*/'前
```
/* not good */
.element {
    color :red! important;
    background-color: rgba(0,0,0,.5);
}

/* good */
.element {
    color: red !important;
    background-color: rgba(0, 0, 0, .5);
}

/* not good */
.element ,
.dialog{
    ...
}

/* good */
.element,
.dialog {

}

/* not good */
.element>.dialog{
    ...
}

/* good */
.element > .dialog{
    ...
}

/* not good */
.element{
    ...
}

/* good */
.element {
    ...
}

/* not good */
@if{
    ...
}@else{
    ...
}

/* good */
@if {
    ...
} @else {
    ...
}
```
***
#### 空行
* 以下几种情况需要空行：

1、文件最后保留一个空行
2、'}'后最好跟一个空行，包括scss中嵌套的规则
3、属性之间需要适当的空行
```
/* not good */
.element {
    ...
}
.dialog {
    color: red;
    &:after {
        ...
    }
}

/* good */
.element {
    ...
}

.dialog {
    color: red;

    &:after {
        ...
    }
}
```
***
#### 换行
* 以下几种情况不需要换行：

1、'{'前
* 以下几种情况需要换行：

1、'{'后和'}'前
2、每个属性独占一行
3、多个规则的分隔符','后
```
/* not good */
.element
{color: red; background-color: black;}

/* good */
.element {
    color: red;
    background-color: black;
}

/* not good */
.element, .dialog {
    ...
}

/* good */
.element,
.dialog {
    ...
}
```
***
#### 注释
* 注释统一用'/* */'（scss中也不要用'//'），具体参照右边的写法；
* 缩进与下一行代码保持一致；
* 可位于一个代码行的末尾，与代码间隔一个空格。

```
/* Modal header */
.modal-header {
    ...
}

/*
 * Modal header
 */
.modal-header {
    ...
}

.modal-header {
  /* 50px */
  width: 50px;

  color: red; /* color red */
}
```
***
#### 引号
* 最外层统一使用双引号；
* url的内容要用引号；
* 属性选择器中的属性值需要引号。

```
.element:after {
    content: "";
    background-image: url("logo.png");
}

li[data-type="single"] {
    ...
}
```
***
#### 命名与设计方法
* 设计原则

1、保持 CSS 便于维护
2、清晰易懂
3、可拓展性/可控性
* 基础命名规则

1、类名使用小写字母，以中划线分隔
2、id采用驼峰式命名
3、scss中的变量、函数、混合、placeholder采用驼峰式命名
* BEM（Block, Element, Modifier）命名法

BEM 命名法可以使得选择器更规范，更清晰，更具语义。
该命名法按照如下格式：


/* class */
.block{}
.block__element{}
.block--modifier{}

其中：
.block 代表某个基本的抽象元素；
.block__element 代表 .block 这一整体的一个子元素；
.block--modifier 代表 .block 的某个不同状态。
打个比方：

.person{}
.person--woman{}
.person__hand{}
.person__hand--left{}
.person__hand--right{}

这个例子中我们描述的基本元素是一个人，然后这个人可能是一个女人。我们还知道人拥有手，这些是人体的一部分，而手也有不同的状态，如同左手与右手。

这样我们就可以根据父元素来划定选择器的命名空间并传达该选择器的职能，这个选择器是一个子元素（__）还是父元素的不同状态（--）？

由此，.page-wrapper 是一个独立的选择器。这是一个符合规范的命名，因为它不是其它元素的子元素或其它状态；然而 .widget-heading 则与其它对象有关联，它应当是 .widget 的子元素，所以我们应当将其重命名为 .widget__heading。

BEM 命名法虽然不太好看，而且相当冗长，但是它使得我们可以通过名称快速获知元素的功能和元素之间的关系。与此同时，BEM 语法中的重复部分非常有利于 cssnano 插件的压缩算法。

无论你是否使用 BEM 命名法，你都应当确保 class 命名得当，力保一字不多、一字不少；将元素命名抽象化以提高复用性（例如 .ui-list，.media）。由此延伸出去的元素命名则要尽量精准（例如 .user-avatar-link）。不用担心 class 名的数量或长度，因为写得好的代码 cssnano 也能有效压缩。

* 面向对象的CSS设计模式
以面向对象 CSS 的方式写代码。把组件分成结构（对象）与外观（拓展）。正如以下分析：

.person{}
.room{}
.room--kitchen{}
.room--bedroom{}
.room--bathroom{}

我们在屋子里有许多房间，它们都有共同的部分：它们都包含地板、天花板、墙壁和门。这些共享的部分我们可以放到一个抽象的 .room{} class 中。不过我们还有其它与众不同的房间：一个厨房可能有地砖，卧室可能有地毯，洗手间可能没有窗户但是卧室会有，每个房间的墙壁颜色也许也会不一样。面向对象 CSS 的思路使得我们把相同部分抽象出来组成结构部分，然后用更具体的 class 来拓展这些特征并添加特殊的处理方法。

所以比起编写大量的特殊模块，应当努力找出这些模块中重复的设计模式并将其抽象出来，写成一个可以复用的 class，将其用作基础然后编写其它拓展模块的特殊情形。

当你要编写一个新组件时，将其拆分成结构和外观。编写结构部分时用最通用 class 以保证复用性，编写外观时用更具体的 class 来添加设计方法。

* 布局

所有组件都不要声明宽度，而由其亲元素或格栅系统来决定。

坚决不要声明高度。高度应当仅仅用于尺寸已经固定的东西，例如图片和 CSS Sprite。在 p，ul，div 等元素上不应当声明高度。如果需要的话可以写 line-height，这个更加灵活。

格栅系统应当当作书架来理解。是它们容纳内容，而不是把它们本身当成内容装起来，正如你先搭起书架再把东西放进去。比起声明它们的尺寸，把格栅系统和元素的其它属性分来开处理更有助于布局，也使得我们的前端工作更高效。

你在格栅系统上不应当添加任何样式，他们仅仅是为布局而用。在格栅系统内部再添加样式。在格栅系统中任何情况下都不要添加盒模型相关属性。

* 避免使用元素选择器

出于两点考虑：
　　第一点，和上一段提到的相关，在HTML中，有很多常用的高频元素，比如，div、p、span、a、ul等。如果，你在多层选择器的最内层使用了元素选择器，那么，在开始寻找时，浏览器就会遍历HTML中的所有该元素，显然，这是没有必要的。

　　第二点，我们的需求和代码结构都是存在着潜在变化的，今天写好了一个页面，明天可能就要再加进去一个按钮，再加进去一句话，再加进去一个图标。我们写好的一个结构，也随时可能被复用到别的结构中去。所以，如果，你使用了元素选择器去定死某个东西，不论是新加进来的东西，还是被复用的东西加到别的结构里去，都极有可能产生样式的冲突，这个时候，你又不得不写多余的样式进行覆盖修正，或者重新定义类。

　　所以，出于以上考虑，在具体的代码模块中，尽量不要使用元素选择器，使用元素选择器的前提是，你完全的确定，不会导致出现问题。注意，我用的限定范围是“具体的代码模块”，那么用于定义通用规则的样式，是可以的，也是推荐使用的，比如，reset。也可以是别的地方，这就需要我们自行考量。

* 使用 CSS 选择器的目的

出于两点考虑：
比起努力运用选择器定位到某元素，更好的办法是直接给你想要添加样式的元素直接添加一个 class。我们以 .header ul{}这样一个选择器为例。

假定这个 ul 就是这个网站的全站导航，它位于 header 中，而且目前为止是 header 中唯一的 ul 元素。.header ul{} 的确可以生效，但是这样并不是好方法，它很容易过时，而且非常晦涩。如果我们在 header 中再添加一个 ul 的话，它就会套用我们给这个导航部分写的样式，哪怕我们设想的不是这个效果。这意味着我们要么要重构许多代码，要么给后面的 ul 新写许多样式来抵消之前的影响。

你的选择器必须符合你要给这个元素添加样式的原因。思考一下，「我定位到这个元素，是因为它是 .header 下的 ul，还是因为它是我的网站导航？」这将决定你应当如何使用选择器。

确保你的核心选择器不是类型选择器，也不是高级对象或抽象选择器。例如你在我们的 CSS 中肯定找不到诸如 .sidebar ul{} 或者 .footer .media{} 这样的选择器。

表达清晰：直接找到你要添加样式的元素，而非其亲元素。不要想当然地认为 HTML 不会改变。用 CSS 直接命中你需要的元素，而非投机取巧。

完整内容请参考Shoot to kill; CSS selector intent

!important
只在起辅助作用的 class 上用 !important。用 !important 提升优先级也可以，例如如果你要让某条规则一直生效的话，可以用 .error{ color:red!important; }。

避免主动使用 !important。例如 CSS 写得很复杂时不要用它来取巧，要好好整理并重构之前的部分，保持选择器简短并且避免用 ID 将效果拔群。

* 魔数与绝对定位

魔数（Magic Number）是指那些「凑巧有效果」的数字，这东西非常不好，因为它们只是治标不治本而且缺乏拓展性。

例如 .dropdown__nav li:hover ul{ top:37px; } 把下拉菜单移动下来远非良策，因为这里的 37px 就是个魔数。37px 会生效的原因是因为这时 .dropbox__nav 碰巧高 37px 而已。

这时你应该用 .dropdown__nav li:hover ul{ top:100%; }，也即无论 .dropbox--down 多高，这个下拉菜单都会往下移动 100%。

每当你要在代码中放入数字的时候，请三思而行。如果你能用一个关键字（例如 top:100% 意即「从上面拉到最下面」）替换之，或者有更好的解决方法的话，就尽量避免直接出现数字。

你在 CSS 中留下的每一个数字，都是你许下而不愿遵守的承诺。

```
/* class */
.element-content {
  ...
}

/* id */
#myDialog {
  ...
}

/* 变量 */
$colorBlack: #000;

/* 函数 */
@function pxToRem($px) {
  ...
}

/* 混合 */
@mixin centerBlock {
  ...
}

/* placeholder */
%myDialog {
  ...
}

/* not good */
.block {
  position: relative;
  ...
}
.block__left {
  position: absolute;
  left: -3.533em;
  width: 3.533em;
  ...
}
.block__right {
  position: absolute;
  right: -3.533em;
  width: 3.533em;
  ...
}
/* good */
.block {
  position: relative;
  ...
}
.block__left {
  position: absolute;
  right: 100%;
  width: 3.533em;
  ...
}
.block__right {
  position: absolute;
  left: 100%;
  width: 3.533em;
  ...
}
```
***
#### 属性声明顺序
* 相关的属性声明按右边的顺序做分组处理，组之间需要有一个空行。

```
.declaration-order {
    display: block;
    float: right;

    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    border: 1px solid #e5e5e5;
    border-radius: 3px;
    width: 100px;
    height: 100px;

    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    text-align: center;

    color: #333;
    background-color: #f5f5f5;

    opacity: 1;
}
// 下面是推荐的属性的顺序
[
    [
        "display",
        "visibility",
        "float",
        "clear",
        "overflow",
        "overflow-x",
        "overflow-y",
        "clip",
        "zoom"
    ],
    [
        "table-layout",
        "empty-cells",
        "caption-side",
        "border-spacing",
        "border-collapse",
        "list-style",
        "list-style-position",
        "list-style-type",
        "list-style-image"
    ],
    [
        "-webkit-box-orient",
        "-webkit-box-direction",
        "-webkit-box-decoration-break",
        "-webkit-box-pack",
        "-webkit-box-align",
        "-webkit-box-flex"
    ],
    [
        "position",
        "top",
        "right",
        "bottom",
        "left",
        "z-index"
    ],
    [
        "margin",
        "margin-top",
        "margin-right",
        "margin-bottom",
        "margin-left",
        "-webkit-box-sizing",
        "-moz-box-sizing",
        "box-sizing",
        "border",
        "border-width",
        "border-style",
        "border-color",
        "border-top",
        "border-top-width",
        "border-top-style",
        "border-top-color",
        "border-right",
        "border-right-width",
        "border-right-style",
        "border-right-color",
        "border-bottom",
        "border-bottom-width",
        "border-bottom-style",
        "border-bottom-color",
        "border-left",
        "border-left-width",
        "border-left-style",
        "border-left-color",
        "-webkit-border-radius",
        "-moz-border-radius",
        "border-radius",
        "-webkit-border-top-left-radius",
        "-moz-border-radius-topleft",
        "border-top-left-radius",
        "-webkit-border-top-right-radius",
        "-moz-border-radius-topright",
        "border-top-right-radius",
        "-webkit-border-bottom-right-radius",
        "-moz-border-radius-bottomright",
        "border-bottom-right-radius",
        "-webkit-border-bottom-left-radius",
        "-moz-border-radius-bottomleft",
        "border-bottom-left-radius",
        "-webkit-border-image",
        "-moz-border-image",
        "-o-border-image",
        "border-image",
        "-webkit-border-image-source",
        "-moz-border-image-source",
        "-o-border-image-source",
        "border-image-source",
        "-webkit-border-image-slice",
        "-moz-border-image-slice",
        "-o-border-image-slice",
        "border-image-slice",
        "-webkit-border-image-width",
        "-moz-border-image-width",
        "-o-border-image-width",
        "border-image-width",
        "-webkit-border-image-outset",
        "-moz-border-image-outset",
        "-o-border-image-outset",
        "border-image-outset",
        "-webkit-border-image-repeat",
        "-moz-border-image-repeat",
        "-o-border-image-repeat",
        "border-image-repeat",
        "padding",
        "padding-top",
        "padding-right",
        "padding-bottom",
        "padding-left",
        "width",
        "min-width",
        "max-width",
        "height",
        "min-height",
        "max-height"
    ],
    [
        "font",
        "font-family",
        "font-size",
        "font-weight",
        "font-style",
        "font-variant",
        "font-size-adjust",
        "font-stretch",
        "font-effect",
        "font-emphasize",
        "font-emphasize-position",
        "font-emphasize-style",
        "font-smooth",
        "line-height",
        "text-align",
        "-webkit-text-align-last",
        "-moz-text-align-last",
        "-ms-text-align-last",
        "text-align-last",
        "vertical-align",
        "white-space",
        "text-decoration",
        "text-emphasis",
        "text-emphasis-color",
        "text-emphasis-style",
        "text-emphasis-position",
        "text-indent",
        "-ms-text-justify",
        "text-justify",
        "letter-spacing",
        "word-spacing",
        "-ms-writing-mode",
        "text-outline",
        "text-transform",
        "text-wrap",
        "-ms-text-overflow",
        "text-overflow",
        "text-overflow-ellipsis",
        "text-overflow-mode",
        "-ms-word-wrap",
        "word-wrap",
        "-ms-word-break",
        "word-break"
    ],
    [
        "color",
        "background",
        "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
        "background-color",
        "background-image",
        "background-repeat",
        "background-attachment",
        "background-position",
        "-ms-background-position-x",
        "background-position-x",
        "-ms-background-position-y",
        "background-position-y",
        "-webkit-background-clip",
        "-moz-background-clip",
        "background-clip",
        "background-origin",
        "-webkit-background-size",
        "-moz-background-size",
        "-o-background-size",
        "background-size"
    ],
    [
        "outline",
        "outline-width",
        "outline-style",
        "outline-color",
        "outline-offset",
        "opacity",
        "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
        "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
        "-ms-interpolation-mode",
        "-webkit-box-shadow",
        "-moz-box-shadow",
        "box-shadow",
        "filter:progid:DXImageTransform.Microsoft.gradient",
        "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
        "text-shadow"
    ],
    [
        "-webkit-transition",
        "-moz-transition",
        "-ms-transition",
        "-o-transition",
        "transition",
        "-webkit-transition-delay",
        "-moz-transition-delay",
        "-ms-transition-delay",
        "-o-transition-delay",
        "transition-delay",
        "-webkit-transition-timing-function",
        "-moz-transition-timing-function",
        "-ms-transition-timing-function",
        "-o-transition-timing-function",
        "transition-timing-function",
        "-webkit-transition-duration",
        "-moz-transition-duration",
        "-ms-transition-duration",
        "-o-transition-duration",
        "transition-duration",
        "-webkit-transition-property",
        "-moz-transition-property",
        "-ms-transition-property",
        "-o-transition-property",
        "transition-property",
        "-webkit-transform",
        "-moz-transform",
        "-ms-transform",
        "-o-transform",
        "transform",
        "-webkit-transform-origin",
        "-moz-transform-origin",
        "-ms-transform-origin",
        "-o-transform-origin",
        "transform-origin",
        "-webkit-animation",
        "-moz-animation",
        "-ms-animation",
        "-o-animation",
        "animation",
        "-webkit-animation-name",
        "-moz-animation-name",
        "-ms-animation-name",
        "-o-animation-name",
        "animation-name",
        "-webkit-animation-duration",
        "-moz-animation-duration",
        "-ms-animation-duration",
        "-o-animation-duration",
        "animation-duration",
        "-webkit-animation-play-state",
        "-moz-animation-play-state",
        "-ms-animation-play-state",
        "-o-animation-play-state",
        "animation-play-state",
        "-webkit-animation-timing-function",
        "-moz-animation-timing-function",
        "-ms-animation-timing-function",
        "-o-animation-timing-function",
        "animation-timing-function",
        "-webkit-animation-delay",
        "-moz-animation-delay",
        "-ms-animation-delay",
        "-o-animation-delay",
        "animation-delay",
        "-webkit-animation-iteration-count",
        "-moz-animation-iteration-count",
        "-ms-animation-iteration-count",
        "-o-animation-iteration-count",
        "animation-iteration-count",
        "-webkit-animation-direction",
        "-moz-animation-direction",
        "-ms-animation-direction",
        "-o-animation-direction",
        "animation-direction"
    ],
    [
        "content",
        "quotes",
        "counter-reset",
        "counter-increment",
        "resize",
        "cursor",
        "-webkit-user-select",
        "-moz-user-select",
        "-ms-user-select",
        "user-select",
        "nav-index",
        "nav-up",
        "nav-right",
        "nav-down",
        "nav-left",
        "-moz-tab-size",
        "-o-tab-size",
        "tab-size",
        "-webkit-hyphens",
        "-moz-hyphens",
        "hyphens",
        "pointer-events"
    ]
]
```
***
#### 颜色
* 颜色16进制用小写字母；
* 颜色16进制尽量用简写。

```
/* not good */
.element {
    color: #ABCDEF;
    background-color: #001122;
}

/* good */
.element {
    color: #abcdef;
    background-color: #012;
}
```
***
#### 属性简写
* 属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以建议尽量分开声明会更加清晰；
* <font color=#d44950>margin</font> 和 <font color=#d44950>padding</font> 相反，需要使用简写；
* 常见的属性简写包括：

1、<font color=#d44950>font</font>
2、<font color=#d44950>background</font>
3、<font color=#d44950>transition</font>
4、<font color=#d44950>animation</font>

```
/* not good */
.element {
    transition: opacity 1s linear 2s;
}

/* good */
.element {
    transition-delay: 2s;
    transition-timing-function: linear;
    transition-duration: 1s;
    transition-property: opacity;
}
```
***
#### SCSS相关
* 提交的代码中不要有 @debug；
* 声明顺序：

1、<font color=#d44950>@extend</font>
2、不包含 <font color=#d44950>@content</font>的 <font color=#d44950>@include</font>
3、包含 <font color=#d44950>@content</font>的 <font color=#d44950>@include</font>
4、自身属性
5、嵌套规则
* <font color=#d44950>@import</font> 引入的文件不需要开头的'_'和结尾的'.scss'；嵌套最多不能超过5层；
* <font color=#d44950>@extend</font> 中使用placeholder选择器；去掉不必要的父级引用符号'&'。

```
/* not good */
@import "_dialog.scss";

/* good */
@import "dialog";

/* not good */
.fatal {
    @extend .error;
}

/* good */
.fatal {
    @extend %error;
}

/* not good */
.element {
    & > .dialog {
        ...
    }
}

/* good */
.element {
    > .dialog {
        ...
    }
}

/* not good */
.header {
    .site-nav {
        .list {
            .button {
                ...
            }
        }
    }
}

/* good */
.header {
}
.site-nav {
    .list {
    }
    .button {
        ...
    }
}
```
***
#### 杂项
* 不允许有空的规则；
* 元素选择器用小写字母；
* 去掉小数点前面的0；
* 去掉数字中不必要的小数点和末尾的0；
* 属性值'0'后面不要加单位；
* 同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；
* 无前缀的标准属性应该写在有前缀的属性后面；
* 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；
* 不要在一个文件里出现两个相同的规则；
* 用 border: 0; 代替 border: none;；
* 选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；
* 发布的代码中不要有 @import；
* 尽量少用'*'选择器。
* 标签选择器处理大多数的通用情况，或者是未知内嵌后代，其余加class 去控制。渲染样式从右到左，右边能匹配到的越多，效率越低
* 直接子选择器，

```
/* not good */
.element {
}

/* not good */
LI {
    ...
}

/* good */
li {
    ...
}

/* not good */
.element {
    color: rgba(0, 0, 0, 0.5);
}

/* good */
.element {
    color: rgba(0, 0, 0, .5);
}

/* not good */
.element {
    width: 50.0px;
}

/* good */
.element {
    width: 50px;
}

/* not good */
.element {
    width: 0px;
}

/* good */
.element {
    width: 0;
}

/* not good */
.element {
    border-radius: 3px;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;

    background: linear-gradient(to bottom, #fff 0, #eee 100%);
    background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
    background: -moz-linear-gradient(top, #fff 0, #eee 100%);
}

/* good */
.element {
    -webkit-border-radius: 3px;
       -moz-border-radius: 3px;
            border-radius: 3px;

    background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
    background:    -moz-linear-gradient(top, #fff 0, #eee 100%);
    background:         linear-gradient(to bottom, #fff 0, #eee 100%);
}

/* not good */
.element {
    color: rgb(0, 0, 0);
    width: 50px;
    color: rgba(0, 0, 0, .5);
}

/* good */
.element {
    color: rgb(0, 0, 0);
    color: rgba(0, 0, 0, .5);
}
```
***
#### 页面信息层级规范(z-index 定值范围)
* 该元素的定位方式，必须为absolute、relative或者fixed
* Popout 弹出层，作为内容层和导航层的补充，用于承载弹窗通知、操作菜单、菜 单、成功或加载中等状态，表单报错提示等弹出内容。组件间互斥。
* Mask 遮罩层，配合弹出层和Popout层使用，用于锁定内容层和导航层操作，基 本不单独使用。
* Navigation 导航层，位于内容层之上，在用户滑动内容层时可保持位置不动，通常用 于承载导航栏等需要固定在页面的元素。
* Content 内容层，承载页面主要内容。
* z-index

1、 Popout 1100-9999
2、 Mask 1050
3、 Navigation 100-199
4、 Content 0-99
* zIndex 组件本身遵循上述规则，组件内部则由1开始，不受约束

```
.content {
    z-index: 0-99;
}
.navigation {
    z-index: 100-199;
}
.mask {
    z-index: 1050;
}
.popout {
    z-index: 1100-9999;
}
```
***
#### 动画与变形
* 无IE使用需求时，尽量用transform变形与动画
* transition，不用all
* 序列帧单独文件存放，便于整体复用
* 动画时间点分解，采用变量方式储存，保证动画时间设置的连贯

```
/* 角色移动 */
/* not good */
.role {
    left: 0;
}
.role {
    left: 50%;
}

/* good */
.parent {
    overflow: hidden;
    .role {
        width: 100%;
        height: 100%;
        transform: translate(0, 0);
    }
    .role {
        transform: translate(50%, 0);
    }
}

/* 时间变量存储 */
/* 情景，小明去超市买东西回来。时间分为3段，去超市路上、选购东西、返程。动画分为2个 */
$markGo: 0.6s;
$markStay: 0.4s;
$markBack: 0.6s;
.ming-go {
    animation: go $markGo linear 0s;
}
.ming-back {
    animation: back $markBack linear $markStay;
}
/* 小明在3个时间段长短任意修改，无伤大雅 */
```
***
#### 特殊字体
* 引入特殊字体文件，字体命名采用字母命名

```
@font-face {
    font-family: HYPED;
    src: url('font/HYPED_Font.otf');
}
.class {
    font-family: Lovelo-Black, sans-serif;
    font-size:24px;
}
```
***
#### 字体图标
* 一般用于纯色的图标，iconfont

```
link rel="stylesheet" type="text/css" href="static/css/iconfont.css"

div class="icon iconfont" :class="icon-xxx"
```
***
#### 按钮多态
* PC端，常态、悬浮、点击、不可点击
* 移动端，常态、点击、不可点击，悬浮态不能写

```
pc
.btn-xxx {
    color: #333;
    &:hover {}
    &:active, &.active {}
    &.disabled {}
}
移动端
.btn-xxx {
    color: #333;
    &:active, &.active {}
    &.disabled {}
}
```
***
#### 清除浮动
* 在父容器加class : clearfix
* 在浮动元素的最后面，加 div —— style="clear: both;"

```
.clearfix:before,
.clearfix:after {
    display: table;
    content: "";
    line-height: 0
}
.clearfix:after {
    clear: both;
}

div style="clear:both;"
```
***
#### 媒体查询
* 尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。
* media外层不套其他class ——？
* 媒体查询常用断点：手机、pad、pc
* IE8 ，9 兼容，引进respond.js

```
/*#region Bootstrap Media Query */

/* 超小屏幕（手机，小于 768px） */

/* 小屏幕（平板，大于等于 768px） */
@media (min-width: 768px) {}

/* 中等屏幕（桌面显示器，大于等于 992px） */
@media (min-width: 992px) {}

/* 大屏幕（大桌面显示器，大于等于 1200px） */
@media (min-width: 1200px) {}

/* screen-xs-max */
@media (max-width: 767px) {}


/* screen-sm-min & screen-sm-max */
@media (min-width: 768px) and (max-width: 991px) {}


/* screen-md-min & screen-md-max */
@media (min-width: 992px) and (max-width: 1199px) {}


/* screen-lg-min */
@media (min-width: 1200px) {}

/*#endregion */

/* IE8、IE 9 的媒体media兼容*/
[if lt IE 9]
script src="../libs/respond.min.js"
[endif]
```
***
#### CSS hack
* 目前最低兼容IE8，hack ： /9
* 采用不同的思路，来比避免hack
* 在头部按需加载，来兼容IE8 ，此情况下可不写hack

```
#test{
    color:red; /* 所有浏览器都支持 */
    color:red !important;/* Firefox、IE7支持 */
    _color:red; /* IE6支持 */
    *color:red; /* IE6、IE7支持 */
    *+color:red; /* IE7支持 */
    color:red\9; /* IE6、IE7、IE8支持 */
    color:red\0; /* IE8支持 */
}
body:nth-of-type(1) p{color:red;} /* Chrome、Safari支持 */

/* 格式自行查找 */
[if IE 8]
link rel="stylesheet" href="../style/style_lowIE.css"
[endif]
```
***
#### 宽度和高度
* 考虑到多语言与适应性，尽量不设置宽高
***