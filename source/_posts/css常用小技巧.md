---
title: css常用小技巧
date: 2019-03-01 19:08:19
categories: 
- 前端学习
tags:
- css
---
一、清除浮动（将元素并排）
    （1）给需并列元素的父级加上class="clearfix"
    （2）给需并列的元素加上css：float:left; / float:right;
    （3）clearfix:after{
                            content="";
                            display:block;
                            clear:both;
            }
        （4）若要使一行只有两个元素，给元素加上：width:50%;（两元素加起来等于100%即可）

二、居中
    1、元素垂直居中（写了高度就要考虑垂直居中）
        （1）使同一个div内的元素中心线对齐：给div加上相同的padding-top和padding-bottom
        （2）若div或span的字：除加上padding-top和padding-bottom以外还需设置行高
                （可与元素高度相同，再加margin）
        （3）行内元素或表格元素垂直居中：
                line-height=height;
    2、元素水平居中：
        （1）块元素居中(需给宽度才可居中):
                 margin-left:auto;
                 margin-right:auto;
                 （margin:0 auto;）
        （2）内联元素居中：
                给父级元素加CSS样式：text-align:center;
        （3）调整padding，margin

三、脱离文档流（使元素悬浮或者固定在一个位置）
（1）position:fixed;
（2）top:0;left:0;（这是定位可以随便定）
（3）宽度会缩起来：若无必要，别用width:100%;

四、背景图片
（1）图片居中：background-position:center center;
（2）图片自适应div：background-size:cover;

五、关于display的三种属性
（1）inline-block能使inline元素拥有高度，并且能并排放置

六、画一个三角形
（1）width:0px;
（2）border-top-width:0;
（3）border:10px solid transparent;
（4）border-color:red;

七、定位方法
    1、绝对定位
    （1）父元素上写position:relative;
    （2）需定位元素上写position:absolute;
    （3）确定位置：top/right/bottom/left:4px;
    
八、左右布局
    1、float+clearfix
   （1）float+clearfix将列表元素调为横向布局（见一）
   （2）列表元素宽度设为50%
    2、绝对定位
    （1）用一个relative父元素包裹住所有元素
    （2）子元素absoulte调整位置

九、左中右布局
    1、float+margin
    （1）左边float:left，中间用margin-left和margin-right，右边float:right
    2、float+absolute
    （1）左边float:left，中间用absolute调整，右边float:right

十、需组合使用的：
   （1） display:inline-block;
             vertical-align:top;
             
十一、状态机
    使用情形：需要可变地切换一个元素的状态时
    实现方法：
    css文件里写入三个状态类xxx-state1,xxx-state2,xxx-state3
    script标签修改 作用对象.className="xxx-state?"
    技巧：配合transition:all 0.2s可让状态切换不显突兀

十二、box-sizing:border-box
    作用：在计算宽度的时候，将border和padding算入其中，使我们写的宽度是加入border、padding后的宽度
    （避免它们撑破父元素，破坏左右布局）
