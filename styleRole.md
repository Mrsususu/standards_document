# 样式规则

> 参考

**Airbnb-css:** <https://github.com/airbnb/css>

**nec:** <http://nec.netease.com/>

## 预处理语言选择
sass
## 全局样式清单

1. css reset相关（选用bootstrap中的Normalize.css）
2. 公共模块：针对于某项目的多功能或多页面可复用的样式集合
3. 通用基础模块：脱离于具体项目，服务于多个项目：grid.css、btn.css、text.css、cell.css、layer.css、icon.css、animation.css

## 代码书写格式

### 1. 书写格式
* 使用 2 个空格作为缩进。
* 在一个规则声明中应用了多个选择器时，每个选择器独占一行。
* 在规则声明的左大括号 { 前加上一个空格。
* 在属性的冒号 : 后面加上一个空格，前面不加空格。
* 规则声明的右大括号 } 独占一行。
* 规则声明之间用空行分隔开。
* 注释单独一行，并使用行注释替代块注释。
* 在使用引号时，采用单引号。

### 2. 内容格式
* 选择器、属性和值都使用小写。
* 十六进制表示颜色，使用小写字母，尽量缩写。
* 省略0时的单位，同时在允许情况下使用0替代none。
* 根据属性重要性书写，按布局、盒模型、文本修饰的顺序来。

## 样式命名规则

### 1. 所有类名格式：
采用"-"作为间隔，命名长度不要过长，最好保证一个类名中"-"数目在三个及以下

### 2. 页面全局布局：
格式为以单字母+“-”作为前缀。
> 参考nec规则
* 布局（grid）（.g-）：将页面分割为几个大块，通常有头部、主体、主栏、侧栏、尾部等。
``` sass
.g-hd {
    // 代表布局的头部
}
.g-bd {
    // 代表布局的主体
}
.g-ft {
    // 代表布局的尾部
}
```
* 模块（module）（.m-）：通常是一个语义化的可以重复使用的较大的整体。比如导航、登录、注册、各种列表、评论、搜索等，也可以为组件。
``` sass
.m-commentModal {
    // 可以代表某评论组件模块
}
```
* 元件（unit）（.u-）：通常是一个不可再分的较为小巧的个体，通常被重复用于各种模块中。比如按钮、输入框、loading、图标等。
* 功能（function）（.f-）：为方便一些常用样式的使用，我们将这些使用率较高的样式剥离出来，按需使用，通常这些选择器具有固定样式表现，比如清除浮动等。不可滥用。
``` sass
.f-cb:after {  // 清除浮动功能
    content:'';
    display:block;
    clear:both;
    overflow:hidden;
    visibility:hidden;
}
```

### 3. 组件内部布局：
使用类前缀，类名+"-"为前缀，类名写成驼峰形式，后面则以功能+"-"+属性为格式。因此命名格式类似于：类名前缀+功能+属性。
	
* 类名前缀在sass中可以通过统一方式完成：
``` sass
$modal-prefix: modal;

.#{$modal-prefix}-container {
    background: XXX;
    ... 
}
```

* 功能部分为模块功能概述。类似于nav/list/header/container等。例如：
``` sass
.modalName-container {
    background: XXX;
    ...
}
.modalName-nav {
    display: XXX;
    ...
}
```
* 属性部分为样式或者状态的描述，或者一些补充信息。类似于left/right/color等。例如：
``` sass
.modalName-nav-left {
    float: XXX;
    ...
}
.modalName-item-hide {
    display: XXX;
    ...
}
```

### 4. 其他：　

在使用 ***“页面全局布局”*** 和 ***“组件内部布局”*** 的大框架下，可以辅助使用一些其他类名。

例如:
``` sass
.mt10 {
    margin-top：10px; // 直观缩写margin-top：10px，用于小范围调整
}
```
``` sass
.modalName-container {
    .mb5 { // 辅助类名建议放置在组件类名下，保证私有性
        margin-bottom：5px;    
    }
}
``` 

这些辅助类名可不严格符合上面两种标准，但需要控制好变量私有性问题，避免全局污染。建议只在局部设计中使用，并同时保证语义化可读性。

## 通用对外开放的组件封装
采用BEM模式。此模式在封装通用组件时候选用，日常开发中考虑到可能存在变量名过和标识符号较多的因素，暂先不引入。
* B:block. 例如: `.btn{}` 代表块级元素
* E:element. 例如: `.btn__price{}` 代表属于上面块级元素的子元素
* M:modifier. 例如: `.btn--orange{}` 代表上面块级元素的样式和状态改变
