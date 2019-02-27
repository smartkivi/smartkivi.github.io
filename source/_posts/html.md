---
title: html
date: 2019-02-27 17:08:58
categories: 
- 前端学习
tags:
- html
---
一、W3C
    万维网联盟（World Wide Web Consortium，W3C），又称W3C理事会，是全球资讯网的主要国际标准组织
    http://www.w3school.com.cn/w3c/w3c_intro.asp

二、MDN
    MDN（Mozilla Developer Network ）是一个 wiki，即意味着任何人都可以向其添加和编辑内容。是一个汇集众多Mozilla基金会产品和网络技术开发文档的免费网站
    https://developer.mozilla.org/zh-CN/

三、HTML常用标签
    1、&#60;a&#62;：
 （1）链接到外部地址：&#60; a href="http://www.mozilla.com/" &#62;
 （2）链接到本页的某个部分：
            &#60;a href="#属性"&#62;
            &#60;img src="https://mdn.mozillademos.org/files/6851/mdn_logo.png" alt="MDN logo"   /&#62;
            &#60;/a&#62;
 （3）创建一个可点击的图片：&#60;a href="https://developer.mozilla.org/en-US/" &#62;
 （4）创建一个email链接：&#60;a href="mailto:nowhere@mozilla.org"&#62;
    2、&#60;audio&#62;：
 （1）播放音频：
            &#60;audio src="http://developer.mozilla.org/@api/deki/files/2926/=AudioTest_(1).ogg" &#62;
    3、&#60;b&#62;：加粗
    4、&#60;button&#62;：
 （1）按钮：&#60;button name="button"&#62;Click me&#60;/button&#62;
    5、&#60;br&#62;：换行
    6、&#60;code&#62;：计算机代码
    7、&#60;dl&#62;&#60;dt&#62;&#60;dd&#62;：表格
    8、&#60;div&#62;：块（contenteditable--是否可修改）
    9、&#60;em&#62;：强调内容
    10、&#60;footer&#62;：元素页脚
    11、&#60;header&#62;：元素头部
    12、&#60;hr&#62;：水平分割线
    13、&#60;h1&#62;-&#60;h6&#62;：标题
    14、&#60;i&#62;:斜体
    15、&#60;img&#62;:
 （1）插入本地图片：&#60;img src="mdn-logo-sm.png" alt="MDN"&#62;
 （2）插入网络图片：
                        &#60;a href="https://developer.mozilla.org/" &#62;
                        &#60;img src="mdn-logo-sm.png" alt="MDN"&#62;&#60;/a&#62;
    16、&#60;input&#62;：
 （1）用户可输入文本的单行输入字段：&#60;input type="text" /&#62;
 （2）可点击的按钮：&#60;input type="button" /&#62;
 （3）复选框：&#60;input type="checkbox" /&#62;
 （4）文件上传：&#60;input type="file" /&#62;
 （5）隐藏字段：&#60;input type="hidden" /&#62;
 （6）图像形式的提交按钮：&#60;input type="image" /&#62; 
 （7）密码字段：&#60;input type="password" /&#62;
 （8）单选按钮：&#60;input type="radio" /&#62; 
 （9）重置按钮：&#60;input type="reset" /&#62; 
 （10）提交按钮：&#60;input type="submit" /&#62; 
    17、&#60;link&#62;
 （1）引入样式表：&#60;link href="style.css" rel="stylesheet"&#62;
    18、&#60;ol&#62;/&#60;ul&#62;&#60;li&#62;：表格
    19、&#60;main&#62;：主题部分
    20、&#60;menu&#62;：
 （1）菜单：
                &#60;menu type="context" id="dropdown-menu"&#62;
                &#60;menuitem label="Action"&#62;
                &#60;menuitem label="Another action"&#62;
                &#60;hr&#62;
                &#60;menuitem label="Separated action"&#62;
                &#60;/menu&#62;
    21、&#60;nav&#62;：导航栏
    22、&#60;output&#62;：
 （1）输出结果：
                &#60;form oninput="result.value=parseInt(a.value)+parseInt(b.value)"&#62;
                &#60;input type="range" name="b" value="50" /&#62; +
                &#60;input type="number" name="a" value="10" /&#62; =
                &#60;output name="result"&#62;&#60;/output&#62;
                &#60;/form&#62;
    23、&#60;p&#62;：段落
    24、&#60;script&#62;：
 （1）嵌入或者引用脚本：&#60;script src="javascript.js"&#62;&#60;/script&#62;
    25、&#60;select&#62;：
 （1）提供选项菜单：
                &#60;select name="select"&#62;
                &#60;option value="value1"&#62;Value 1&#60;/option&#62; 
                &#60;option value="value2" selected&#62;Value 2&#60;/option&#62;
                &#60;option value="value3"&#62;Value 3&#60;/option&#62;
                &#60;/select&#62;
    26、&#60;span&#62;：区分样式
    27、&#60;strong&#62;：表强调作用
    28、&#60;style&#62;：插入css内容
    29、&#60;td&#62;&#60;th&#62;&#60;tr&#62;：表格
    30、&#60;canvas&#62;：画图
四、空元素
    一个空元素（empty element）可能是 HTML，SVG，或者 MathML 里的一个不可能存在子节点（例如内嵌的元素或者元素内的文本）的element。
    例子：&#60;area&#62;、&#60;base&#62;、&#60;br&#62;、&#60;col&#62;、&#60;colgroup&#62; when the span is present、&#60;command&#62;、&#60;embed&#62;、&#60;hr&#62;、&#60;img&#62;、&#60;input&#62;、&#60;keygen&#62;、&#60;link&#62;、&#60;meta&#62;、&#60;param&#62;、&#60;source&#62;、&#60;track&#62;、&#60;wbr&#62;

五、可替换元素
    可替换元素（replaced element）的展现效果不是由 CSS 来控制的。这些元素是一种外部对象，它们外观的渲染，是独立于 CSS 的。简单来说，它们的内容不受当前文档的样式的影响。CSS 可以影响可替换元素的位置，但不会影响到可替换元素自身的内容。
    例子：&#60;iframe&#62;、&#60;video&#62;、&#60;embed&#62;、&#60;img&#62;，在特殊情况下，下列元素可作为可替换元素处理：&#60;option&#62;、&#60;audio&#62;、&#60;canvas&#62;、&#60;object&#62;、&#60;applet&#62;

六、若想在html页面中打出标签，需用<span>"&#60</span><span>;"</span><span>"&#62</span><span>;"</span>"代替"<"">"

