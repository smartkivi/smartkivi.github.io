---
title: DOM
date: 2019-04-08 13:06:53
categories: 
- 前端学习
tags:
- DOM
---
DOM1级定义了一个Node接口，该接口由DOM中所有节点类型实现。这个Node接口在JS中是作为Node类型实现的。在IE9以下版本无法访问到这个类型，JS中所有节点都继承自Node类型，都共享着相同的基本属性和方法。

一、Node类型概述

Node有一个属性nodeType表示Node的类型，它是一个整数，其数值分别表示相应的Node类型，具体如下：

Node.ELEMENT_NODE:1

Node.TEXT_NODE:3

Node.PROCESSING_INSTRUCTION_NODE:7

Node.COMMENT_NODE:8

Node.DOCUMENT_NODE:9

Node.DOCUMENT_TYPE_NODE:10

Node.DOCUMENT_FRAGMENT_NODE:11

HTML中的节点并不只是包括元素节点，它还包括文本节点，注释节点等等。

假设我们要判断一个元素是文字还是节点，我们通过下式来判断：Node.nodeType ===1



二、常用的Node类型

1、Element类型

Element提供了对元素标签名，子节点和特性的访问，我们常用HTML元素比如div，span，a等标签就是element中的一种。Element有下面几条特性：

（1）nodeType为1

（2）nodeName为元素标签名，tagName也是返回标签名

（3）nodeValue为null

（4）parentNode可能是Document或Element

（5）子节点可能是Element，Text，Comment，Processing_Instruction，CDATASection或EntityReference

2、Text类型

Text表示文本节点，它包含的是纯文本内容，不能包含html代码，但可以包含转义后的html代码。Text有下面的特性：

（1）nodeType为3

（2）nodeName为#text

（3）nodeValue为文本内容

（4）parentNode是一个Element

（5）没有子节点

3、Comment类型

Comment表示HTML文档中的注释，它有下面的几种特征：

（1）nodeType为8

（2）nodeName为#comment

（3）nodeValue为注释的内容

（4）parentNode可能是Document或Element

（5）没有子节点

4、Document类型

Document表示文档，在浏览器中，document对象是HTMLDocument的一个实例，表示整个页面，它同时也是   window对象的一个属性。Document有下面的特性：

（1）nodeType为9

（2）nodeName为#document

（3）nodeValue为null

（4）parentNode为null

（5）子节点可能是一个DocumentType或Element

5、DocumentFragment类型

DocumentFragment是所有节点中唯一一个没有对应标记的类型，它表示一种轻量级的文档，可能当作一个临时的仓库用来保存可能会添加到文档中的节点。DocumentFragment有下面的特性：

（1）nodeType为11

（2）nodeName为#document-fragment

（3）nodeValue为null

（4）parentNode为null



三、创建型API

1、createElement

createElement通过传入指定的一个标签名来创建一个元素，如果传入的标签名是一个未知的，则会创建一个自定义的标签，注意：IE8以下浏览器不支持自定义标签。

使用如下：

vardiv=document.createElement("div");

使用createElement要注意：通过createElement创建的元素并不属于html文档，它只是创建出来，并未添加到html文档中，要调用appendChild或insertBefore等方法将其添加到HTML文档树中。

2、createTextNode

createTextNode用来创建一个文本节点，用法如下：

vartextNode =document.createTextNode("一个TextNode");

createTextNode接收一个参数，这个参数就是文本节点中的文本，和createElement一样，创建后的文本节点也只是独立的一个节点，同样需要appendChild将其添加到HTML文档树中

3、cloneNode

cloneNode是用来返回调用方法的节点的一个副本，它接收一个bool参数，用来表示是否复制子元素，使用如下：

varparent= document.getElementById("parentElement");

varparent2= parent.cloneNode(true);//传入true

parent2.id ="parent2";

这段代码通过cloneNode复制了一份parent元素，其中cloneNode的参数为true，表示parent的子节点也被复制，如果传入false，则表示只复制了parent节点。

这里有几点要注意：

（1）和createElement一样，cloneNode创建的节点只是游离有html文档外的节点，要调用appendChild方法才能添加到文档树中

（2）如果复制的元素有id，则其副本同样会包含该id，由于id具有唯一性，所以在复制节点后必须要修改其id

（3）调用接收的bool参数最好传入，如果不传入该参数，不同浏览器对其默认值的处理可能不同

除此之外，我们还有一个需要注意的点：

如果被复制的节点绑定了事件，则副本也会跟着绑定该事件吗？这里要分情况讨论：

（1）如果是通过addEventListener或者比如onclick进行绑定事件，则副本节点不会绑定该事件

（2）如果是内联方式绑定的话，副本节点同样会触发事件。

4、createDocumentFragment

createDocumentFragment方法用来创建一个DocumentFragment。在前面我们说到DocumentFragment表示一种轻量级的文档，它的作用主要是存储临时的节点用来准备添加到文档中。

createDocumentFragment方法主要是用于添加大量节点到文档中时会使用到。假设要循环一组数据，然后创建多个节点添加到文档中

使用如下：

document.getElementById("btnAdd").onclick= function(){

varlist=document.getElementById("list");

for(vari= 0;i < 100; i++){

varli= document.createElement("li");

li.textContent = i;

list.appendChild(li);

}

}

这段代码将按钮绑定了一个事件，这个事件创建了100个li节点，然后依次将其添加HTML文档中。这样做有一个缺点：每次一创建一个新的元素，然后添加到文档树中，这个过程会造成浏览器的回流。所谓回流简单说就是指元素大小和位置会被重新计算，如果添加的元素太多，会造成性能问题。这个时候，就是使用createDocumentFragment了。

DocumentFragment不是文档树的一部分，它是保存在内存中的，所以不会造成回流问题。我们修改上面的代码如下：

document.getElementById("btnAdd").onclick=function(){

varlist=document.getElementById("list");

varfragment =document.createDocumentFragment();

for(vari=0;i <100; i++){

varli=document.createElement("li");

li.textContent = i;

fragment.appendChild(li);

}

list.appendChild(fragment);

}

优化后的代码主要是创建了一个fragment，每次生成的li节点先添加到fragment，最后一次性添加到list

5、创建型API总结

创建型api主要包括createElement，createTextNode，cloneNode和createDocumentFragment四个方法，需要注意下面几点：

（1）它们创建的节点只是一个孤立的节点，要通过appendChild添加到文档中

（2）cloneNode要注意如果被复制的节点是否包含子节点以及事件绑定等问题

（3）使用createDocumentFragment来解决添加大量节点时的性能问题



四、页面修改型API

修改页面内容的api主要包括：appendChild，insertBefore，removeChild，replaceChild。

1、appendChild

appendChild我们在前面已经用到多次，就是将指定的节点添加到调用该方法的节点的子元素的末尾。调用方法如下：

parent.appendChild(child);

child节点将会作为parent节点的最后一个子节点。

appendChild这个方法很简单，但是还有有一点需要注意：如果被添加的节点是一个页面中存在的节点，则执行后这个节点将会添加到指定位置，其原本所在的位置将移除该节点，也就是说不会同时存在两个该节点在页面上，相当于把这个节点移动到另一个地方。如果child绑定了事件，被移动时，它依然绑定着该事件。

2、insertBefore

insertBefore用来添加一个节点到一个参照节点之前，用法如下：

parentNode.insertBefore(newNode,refNode);

parentNode表示新节点被添加后的父节点

newNode表示要添加的节点

refNode表示参照节点，新节点会添加到这个节点之前

和appendChild一样，如果插入的节点是页面上的节点，则会移动该节点到指定位置，并且保留其绑定的事件。

关于第二个参数参照节点还有几个注意的地方：

（1）refNode是必传的，如果不传该参数会报错

（2）如果refNode是undefined或null，则insertBefore会将节点添加到子元素的末尾

3、removeChild

removeChild顾名思义，就是删除指定的子节点并返回，用法如下：

vardeletedChild= parent.removeChild(node);

deletedChild指向被删除节点的引用，它等于node，被删除的节点仍然存在于内存中，可以对其进行下一步操作。

注意：如果被删除的节点不是其子节点，则程序将会报错。我们可以通过下面的方式来确保可以删除：

if(node.parentNode){

node.parentNode.removeChild(node);

}

通过节点自己获取节点的父节点，然后将自身删除。

4、replaceChild

replaceChild用于使用一个节点替换另一个节点，用法如下

parent.replaceChild(newChild,oldChild);

newChild是替换的节点，可以是新的节点，也可以是页面上的节点，如果是页面上的节点，则其将被转移到新的位置，oldChild是被替换的节点。

5、页面修改型API总结

页面修改型api主要是这四个接口，要注意几个特点：

（1）不管是新增还是替换节点，如果新增或替换的节点是原本存在页面上的，则其原来位置的节点将被移除，也就是说同一个节点不能存在于页面的多个位置

（2）节点本身绑定的事件会不会消失，会一直保留着。



五、节点查询型API

1、document.getElementById

这个接口根据元素id返回元素，返回值是Element类型，如果不存在该元素，则返回null。

使用这个接口有几点要注意：

（1）元素的Id是大小写敏感的，一定要写对元素的id

（2）HTML文档中可能存在多个id相同的元素，则返回第一个元素

（3）只从文档中进行搜索元素，如果创建了一个元素并指定id，但并没有添加到文档中，则这个元素是不会被查找到的

2、document.getElementsByTagName

这个接口根据元素标签名获取元素，返回一个即时的HTMLCollection类型，什么是即时的HTMLCollection类型呢？HTMLCollcetion元素是即时的表示该集合是随时变化的，也就是是文档中有几个div，它会随时进行变化，当我们新增一个div后，再访问HTMLCollection时，就会包含这个新增的div。

使用document.getElementsByTagName这个方法有几点要注意：

（1）如果要对HTMLCollection集合进行循环操作，最好将其长度缓存起来，因为每次循环都会去计算长度，暂时缓存起来可以提高效率

（2）如果没有存在指定的标签，该接口返回的不是null，而是一个空的HTMLCollection

（3）“*”表示所有标签

3、document.getElementsByName

getElementsByName主要是通过指定的name属性来获取元素，它返回一个即时的NodeList对象。

使用这个接口主要要注意几点：

（1）返回对象是一个即时的NodeList，它是随时变化的

（2）在HTML元素中，并不是所有元素都有name属性，比如div是没有name属性的，但是如果强制设置div的name属性，它也是可以被查找到的



（3）在IE中，如果id设置成某个值，然后传入getElementsByName的参数值和id值一样，则这个元素是会被找到的，所以最好不好设置同样的值给id和name

4、document.getElementsByClassName

这个API是根据元素的class返回一个即时的HTMLCollection，用法如下

varelements =document.getElementsByClassName(names);

这个接口有下面几点要注意：

（1）返回结果是一个即时的HTMLCollection，会随时根据文档结构变化

（2）IE9以下浏览器不支持

（3）如果要获取2个以上classname，可传入多个classname，每个用空格相隔，例如

varelements =document.getElementsByClassName("test1 test2");

5、document.querySelector和document.querySelectorAll

这两个api很相似，通过css选择器来查找元素，注意选择器要符合CSS选择器的规则。

（1）document.querySelector。

document.querySelector返回第一个匹配的元素，如果没有匹配的元素，则返回null。

document.querySelectorAll的不同之处在于它返回的是所有匹配的元素，而且可以匹配多个选择符

要注意两点：

（1）querySelectorAll也是通过深度优先搜索，搜索的元素顺序和选择器的顺序无关

（2）返回的是一个非即时的NodeList，也就是说结果不会随着文档树的变化而变化

兼容性问题：querySelector和querySelectorAll在ie8以下的浏览器不支持。



六、节点关系型api

在html文档中的每个节点之间的关系都可以看成是家谱关系，包含父子关系，兄弟关系等等。

1、父关系型api

parentNode：每个节点都有一个parentNode属性，它表示元素的父节点。Element的父节点可能是Element，Document或DocumentFragment。

parentElement：返回元素的父元素节点，与parentNode的区别在于，其父节点必须是一个Element，如果不是，则返回null

2、兄弟关系型api

previousSibling：节点的前一个节点，如果该节点是第一个节点，则为null。注意有可能拿到的节点是文本节点或注释节点，与预期的不符，要进行处理一下。

previousElementSibling：返回前一个元素节点，前一个节点必须是Element，注意IE9以下浏览器不支持。

nextSibling：节点的后一个节点，如果该节点是最后一个节点，则为null。注意有可能拿到的节点是文本节点，与预期的不符，要进行处理一下。

nextElementSibling：返回后一个元素节点，后一个节点必须是Element，注意IE9以下浏览器不支持。



3、子关系型api

childNodes：返回一个即时的NodeList，表示元素的子节点列表，子节点可能会包含文本节点，注释节点等。

children：一个即时的HTMLCollection，子节点都是Element，IE9以下浏览器不支持。

firstNode：第一个子节点

lastNode：最后一个子节点

hasChildNodes方法：可以用来判断是否包含子节点。



七、元素属性型api

1、setAttribute

setAttribute：根据名称和值修改元素的特性，用法如下。

element.setAttribute(name,value);

其中name是特性名，value是特性值。如果元素不包含该特性，则会创建该特性并赋值。

如果元素本身包含指定的特性名为属性，则可以世界访问属性进行赋值，比如下面两条代码是等价的：

（1）element.setAttribute("id","test");

（2）element.id ="test";

2、getAttribute

getAttribute返回指定的特性名相应的特性值，如果不存在，则返回null或空字符串。用法如下：

varvalue= element.getAttribute("id");



八、元素样式型api

1、window.getComputedStyle

window.getComputedStyle是用来获取应用到元素后的样式，假设某个元素并未设置高度而是通过其内容将其高度撑开，这时候要获取它的高度就要用到getComputedStyle，用法如下：

varstyle =window.getComputedStyle(element[, pseudoElt]);

element是要获取的元素，pseudoElt指定一个伪元素进行匹配。

返回的style是一个CSSStyleDeclaration对象。通过style可以访问到元素计算后的样式

2、getBoundingClientRect

getBoundingClientRect用来返回元素的大小以及相对于浏览器可视窗口的位置，用法如下：

varclientRect= element.getBoundingClientRect();

clientRect是一个DOMRect对象，包含left，top，right，bottom，它是相对于可视窗口的距离，滚动位置发生改变时，它们的值是会发生变化的。除了IE9以下浏览器，还包含元素的height和width等数据，具体可查看链接



参考网址：

http://luopq.com/2015/11/30/javascript-dom/
