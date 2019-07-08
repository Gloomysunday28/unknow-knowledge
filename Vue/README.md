## Vue

### 前言
```
  vue是目前主流的三大框架之一, 拥有丰富的API, 是响应式, 组件化库, 深受大家喜爱
```

### 以下是Vue常见的几个问题
- vue属性abstract是什么?
- vue祖孙之间的传值是怎么传的?
- vue能否提取出像React一样的高阶组件?
- vue怎么引入全部的基本组件?
- vue怎么实现异步组件?
- vue是怎么实现递归组件?
- vue为什么可以在不注册keep-alive的情况下直接使用keep-alive?
- vue是怎么做到监听数组变化?
- vue对于prop和data之间的监听是怎么样的?
- vue是怎么规定props、methods、data之间命名空间的优先级?
- vue生命周期能否是数组形式?
- v-model究竟做了什么?
- vue.extend和new vue的区别是什么?
- vue computed与watch的区别是什么?
- vue data里是否可以直接使用props
```
  可以, prop初始化在data之前
```
- vue data的第一个参数是什么?
```
  vue实例
```
- vue初始化data是在哪两个声明周期之间?
```
  beforeCreated与created
```
- vue v-if与v-show具体区别是什么? 为什么transition组件能够使用v-if来过渡
```
  v-if: 不渲染该组件, 并且在true的时候会重新加载一次生命周期
  v-show: 不显示组件
  
  transition组件会在过渡完之后再销毁组件
```
- vue 在组件触发事件需要添加什么修饰符?
```
  native
```
- vue 哪个修饰符可以优化滚动?
```
  passive
```
- vue key如果是索引值会造成什么后果?
```
  vue key是采用就地复用的原则
```
- vue 为什么无法代理以_ $开头的变量?
```
  与vue内部自身变量可能会产生冲突
```
- vue name具体有什么用?
```
  1. 组件名称, 在vue初始化时会自动注册该组件, 所以可以在该组件里直接使用该组件
  2. keep-alive使用
```
- vue compiler有什么用?
```
  可以独立于其他打包工具来解析vue文件, 也就是可以在不使用webpack工具直接使用vue
```