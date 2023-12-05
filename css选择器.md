## 关于CSS的选择器使用
* p{属性}
* 标签，标签{}
* .class{}
* #id{}
* p.class{} 
元素中的类进行渲染 
* 标签 嵌套标签{}
对标签中的嵌套标签进行渲染
* 标签+标签{} 
和第二个有什么区别？
* 标签属性选择器 
1. 这组选择器根据一个元素上的某个标签的属性的存在以选择元素的不同方式：`[title] { }`
2. 根据一个有特定值的标签属性是否存在来选择:`p::first-line { }
` 
* [伪类](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors) 
* [属性选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors)

## 继承与优先级 
1. 类比标签的优先级高
2. 后出的标签比先出的标签优先级高 
## 属性 
* [border](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)
* [background-image](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image) 
background-image:url("")
## 函数 
* [calc](https://developer.mozilla.org/zh-CN/docs/Web/CSS/calc) 
计算函数 进行简单的四则运算
* [transformer](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform)
旋转 
## @规则 
1. @import"" 
引入外部样式
2. @media 
查询设备，进而调整宽度