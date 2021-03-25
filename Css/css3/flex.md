# Flex 布局
* Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性

## Flex 容器(采用 Flex 布局的元素)
|  容器属性  |  属性值  |  描述  
|   --  | -- | -- 
|  display        | flex, inline-flex | 
| flex-direction  | row, row-reverse , column , column-reverse                    | 属性决定主轴的方向（即项目的排列方向） 
| flex-warp       | nowarp, warp, warp-reverse                                    | 轴线如何换行 
| flex-flow       | flex-direction 与 flex-wrap的简写                              | 是flex-direction属性和flex-wrap属性的简写形式
| justify-content | flex-start, flex-end, center, space-between,space-around      | 主轴上的对齐方式
| algin-items     | flex-start, flex-end, center, baseline, stretch               | 交叉轴上如何对齐
| align-content   | flex-start,flex-end,center,space-between,space-around,stretch | 了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

## Flex 项目(容器的所有子元素自动成为容器成员)
|  项目属性  |  属性值  |  描述  
|   --  | -- | --  
| order        | number    | 定义项目的排列顺序。数值越小，排列越靠前，默认为0 
| flex-grow    | number    | 定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大 
| flex-shrink  | number    | 定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
| flex-basis   | (length或者auto);    | 定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小 
| flex         | none      | 是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。(该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值)
| align-self   | auto,flex-start,flex-end,center,baseline, stretch    | 允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性.默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch
