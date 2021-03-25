# React 
## React diff算法
1. 算法策略
> 针对树结构(tree diff)：对UI层的DOM节点跨层级的操作进行忽略。（数量少）
> 针对组件结构(component diff)：拥有相同类的两个组件生成相似的树形结构，拥有不同类的两个组件会生成不同的属性结构。
> 针对元素结构(element-diff): 对于同一层级的一组节点，使用具有唯一性的id区分 (key属性)

## React setState同步更新
* 为了提高性能React将setState设置为批次更新，即是异步操作函数
* 由React控制的事件处理程序，以及生命周期函数调用setState不会同步更新state 

React控制之外的事件中调用setState是同步更新的。比如原生js绑定的事件(addEventListener), setTimeout/setInterval等。

### React是怎样控制异步和同步的呢？
* React 的 setState 函数实现中，会根据一个变量 isBatchingUpdates 判断是直接更新 this.state 还是放到队列中延时更新，而 isBatchingUpdates 默认是 false，表示 setState 会同步更新 this.state；但是，有一个函数 batchedUpdates，该函数会把 isBatchingUpdates 修改为 true，而当 React 在调用事件处理函数之前就会先调用这个 batchedUpdates将isBatchingUpdates修改为true，这样由 React 控制的事件处理过程 setState 不会同步更新 this.state。

## React Fiber Fiber架构就是为了解决这个问题
* Fiber实现了自己的组件调用栈，它以链表的形式遍历组件树，可以灵活的暂停、继续和丢弃执行的任务。实现方式是使用了浏览器的requestIdleCallback这一 API。
* 改变了之前react的组件渲染机制，新的架构使原来同步渲染的组件现在可以异步化，可中途中断渲染，执行更高优先级的任务。释放浏览器主线程，
> window.requestIdleCallback()会在浏览器空闲时期依次调用函数，这就可以让开发者在主事件循环中执行后台或低优先级的任务，而且不会对像动画和用户交互这些延迟触发但关键的事件产生影响。函数一般会按先进先调用的顺序执行，除非函数在浏览器调用它之前就到了它的超时时间。

# Angular vs. React vs. Vue 前端框架对比
> 一个是 UI 库（React），另一个是成熟的前端框架（Angular），而其中最年轻的（Vue）则可以称之为渐进式框架。

