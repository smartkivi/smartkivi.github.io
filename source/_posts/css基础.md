---
title: css基础
date: 2019-03-01 19:08:04
categories: 
- 前端学习
tags:
- css
---
一、css学习资源
（1）Google: 关键词 MDN
（2）CSS Tricks：https://css-tricks.com/
（3）阮一峰博客：https://www.google.com/search?q=%E9%98%AE%E4%B8%80%E5%B3%B0+css
（4）张鑫旭博客：https://www.zhangxinxu.com/wordpress/category/css/page/25/
（5）Codrops（CSS效果）：https://tympanus.net/codrops/category/playground/
（6）CSS揭秘：http://www.ituring.com.cn/book/1695
（7）CSS2.1：http://cndevdocs.com/
（8）magic of CSS：https://adamschwartz.co/magic-of-css/
（9）wall haven（找壁纸）：https://alpha.wallhaven.cc/
（10）iconfont（找图标）：https://www.iconfont.cn/

二、引用CSS的四种方式
（1）内联样式（style属性）：#60; a style="color:white;" #62;
（2）style标签法（在head标签内style标签）：#60;style#62; div{color:white;}#60;/style#62;
（3）外部样式表：#60;link rel="stylesheet" href="#" #62;
（4）在（3）的基础上CSS嵌套：@input url("#");

三、一些可改动的标签初始属性
（1）ul的小圆点：list-style:none;
（2）body的空隙8px：body{padding:0;margin:0}(也可用*)
（3）a标签链接去除下划线：text-decoration:none;

四、一些可能会用到的属性
（1）text-align:使子代的内联元素居中
（2）#60;span#62;用line-height控制高度
（3）用max-width控制#60;div#62;宽度比较好，还能自适应窗口大小
（4）使border变成圆形：border-radius:50%;
（5）a标签的download属性强制下载

五、容易出bug的地方
（1）height:XXX;
（2）width:100%;

六、需要注意的地方
（1）width的默认值为auto
        width:auto：父元素的content = 子元素（content + padding + border + margin )
        width:100%： 父元素的content = 子元素的content
（2）content-box和border-box
        content-box 的 width 不包括 padding 和 border
        border-box 的 width 包括 padding 和 border

七、伪类和伪元素
    （1）伪类（:）：伪类被添加到一个选择器末尾的关键字，当你希望样式在特定状态下才被呈现到指定的元素时，你可以往元素的选择器后面加上对应的伪类
                :after、:hover
    （2）伪元素（::）： 伪元素添加到选择器，但不是描述特殊状态，它们允许您为元素的某些部分设置样式。
                ::before、::after
