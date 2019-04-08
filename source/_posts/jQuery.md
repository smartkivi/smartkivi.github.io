---
title: jQuery
date: 2019-04-08 13:14:17
categories: 
- 前端学习
tags:
- jQuery
---
window.jQuery = function(nodeOrSelector) {

let nodes = { }

if(typeof nodeOrSelector === 'string'){

let temp = document.querySelectorAll(nodeOrSelector)

for (let i = 0; i < temp.length; i ++){

nodes[i] = temp[i]

}

nodes,length = temp.length

}else if (nodeOrSelector instanceof Node){

nodes = {

0: nodeOrSelector,

length: 1

}

}

nodes.addClass = function(value){

for (let i=0;i

nodes[i].classList.add(value)

}

}

nodes.setText = function(text){

for (let i = 0;i < nodes.length; i++){

nodes[i].textContent = text

}

}

return nodes

}

}

window.$ = jQuery

var $div = $('div')

$div.addClass('red') // 可将所有 div 的 class 添加一个 red

$div.setText('hi') // 可将所有 div 的 textContent 变为 hi



细节：

1、创建一个window对象下的jQuery函数，返回值为对应函数

2、判断传入参数是字符串还是node对象，如果是字符串，则用querySelectorAll选择所有节点，转换为node对象

3、对所有节点进行遍历，修该textContent属性或者添加class
