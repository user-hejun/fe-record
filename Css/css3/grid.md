# Grid 布局
* Flex 布局是轴线布局，只能指定"项目"针对轴线的位置，可以看作是一维布局。Grid 布局则是将容器划分成"行"和"列"，产生单元格，然后指定"项目所在"的单元格，可以看作是二维布局。Grid 布局远比 Flex 布局强大。

## Grid 容器(采用 Grid 布局的元素)
|  容器属性  |  属性值  |  描述 
|   --  | -- | -- 
|  display | grid, inline-grid | 
|  grid-template-columns | number, repeat, auto-fill, fr, minmax, auto |  定义每一列的列宽
|  grid-template-rows | number, repeat, auto-fill, fr, minmax, auto | 定义每一行的行高
|  row-gap |  | 设置行与行的间隔（行间距）
|  column-gap |  | 设置列与列的间隔（列间距）
|  gap |  grid-row-gap & grid-column-gap | row-gap属性和column-gap属性的合并简写形式
|  grid-template-areas |  |
|  grid-auto-flow  | row, columns |
|  justify-items  |  start,end,center,stretch  | 设置单元格内容的水平位置（左中右）
|  align-items  | start,end,center,stretch  | 设置单元格内容的垂直位置（上中下）
|  place-items  | align-items & justify-items | align-items属性和justify-items属性的合并简写形式
|  justify-content  | start,end,center,stretch, space-around,space-between,space-evenly  | 是整个内容区域在容器里面的水平位置（左中右）
|  align-content  | start,end,center,stretch,space-around,space-between,space-evenly | 整个内容区域的垂直位置（上中下）
|  place-content  | align-content & justify-content | 是align-content属性和justify-content属性的合并简写形式
|  grid-auto-columns  | number | 设置浏览器自动创建的多余网格的列宽
|  grid-auto-rows  | number | 设置浏览器自动创建的多余网格的行高
|  grid-template  |  | 是grid-template-columns、grid-template-rows和grid-template-areas这三个属性的合并简写形式
|  grid  |  | 是grid-template-rows、grid-template-columns、grid-template-areas、 grid-auto-rows、grid-auto-columns、grid-auto-flow这六个属性的合并简写形式


## Grid 项目
|  项目属性  |  属性值  |  描述  
|   --  | -- | -- 
|  grid-column-start |  | 左边框所在的垂直网格线
|  grid-column-end |  | 右边框所在的垂直网格线
|  grid-row-start |  | 上边框所在的水平网格线
|  grid-row-end |  | 下边框所在的水平网格线
|  grid-column |  | 是grid-column-start和grid-column-end的合并简写形式
|  grid-column |  | 是grid-column-start和grid-column-end的合并简写形式
|  grid-row |  | 是grid-row-start属性和grid-row-end的合并简写形式
|  grid-area |  | 指定项目放在哪一个区域。
|  justify-self | start, end, center, stretch | 设置单元格内容的水平位置（左中右），跟justify-items属性的用法完全一致，但只作用于单个项目
|  align-self | start, end, center, stretch | 设置单元格内容的水平位置（左中右），跟align-items属性的用法完全一致，但只作用于单个项目
|  place-self | [align-self, justify-self] | 是align-self属性和justify-self属性的合并简写形式