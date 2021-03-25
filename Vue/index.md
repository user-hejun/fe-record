# Vue 详解

## this.$nextTick 的原理和用途
原理
>1. vue用异步队列的方式来控制DOM更新和nextTick回调先后执行
>2. microtask因为其高优先级特性，能确保队列中的微任务在一次事件循环前被执行完毕
>3. 因为兼容性问题，vue不得不做了microtask向macrotask的降级方案

用途
>1. 在Vue生命周期的created()钩子函数进行的DOM操作一定要放在Vue.nextTick()的回调函数中
> 2. 在数据变化后要执行的某个操作，而这个操作需要使用随数据改变而改变的DOM结构的时候，这个操作都应该放进Vue.nextTick()的回调函数中。