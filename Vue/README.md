## Vue

### 前言
```
  vue是目前主流的三大框架之一, 拥有丰富的API, 是响应式, 组件化库, 深受大家喜爱
```

### 以下是Vue常见的几个问题
- vue属性abstract是什么?
```
  抽象组件, 在渲染真实Dom的时候不会渲染
```
- vue祖孙之间的传值是怎么传的?
```
  1. provide & inject
  2. $attrs & $listeners
  3. eventbus
```
- vue能否提取出像React一样的高阶组件?
```
  可以的
```
``` javascript
  export default {
    name: 'HocComponent',
    abstract: true,
    render() {
      const vnode = this.$slots.default
      // 可以在这里做一些逻辑复用
      ...
      return vnode
    }
  }
```
- vue怎么引入全部的基本组件?
``` javascript
  const requireComponent = require.context(
    // 其组件目录的相对路径
    './components',
    // 是否查询其子目录
    false,
    // 匹配基础组件文件名的正则表达式
    /Base[A-Z]\w+\.(vue|js)$/
  )

  requireComponent.keys().forEach(fileName => {
    // 获取组件配置
    const componentConfig = requireComponent(fileName)

    // 获取组件的 PascalCase 命名
    const componentName = upperFirst(
      camelCase(
        // 获取和目录深度无关的文件名
        fileName
          .split('/')
          .pop()
          .replace(/\.\w+$/, '')
      )
    )

    // 全局注册组件
    Vue.component(
      componentName,
      // 如果这个组件选项是通过 `export default` 导出的，
      // 那么就会优先使用 `.default`，
      // 否则回退到使用模块的根。
      componentConfig.default || componentConfig
    )
  })
```
- vue怎么实现异步组件?
``` javascript
  const AsyncComponent = () => ({
    // 需要加载的组件 (应该是一个 `Promise` 对象)
    component: import('./MyComponent.vue'),
    // 异步组件加载时使用的组件
    loading: LoadingComponent,
    // 加载失败时使用的组件
    error: ErrorComponent,
    // 展示加载时组件的延时时间。默认值是 200 (毫秒)
    delay: 200,
    // 如果提供了超时时间且组件加载也超时了，
    // 则使用加载失败时使用的组件。默认值是：`Infinity`
    timeout: 3000
  })

  // 如果希望在vue-router里使用, 必须是在版本v2.4.0+使用
```
- vue是怎么实现递归组件?
``` javascript
  // tree-foler.js
  <p>
    <span>{{ folder.name }}</span>
    <tree-folder-contents :children="folder.children"/>
  </p>

  // tree-folder-contents.js:
  <ul>
    <li v-for="child in children">
      <tree-folder v-if="child.children" :folder="child"/>
      <span v-else>{{ child.name }}</span>
    </li>
  </ul>

  // 由于以上模块是互相引用, webpack无法解析出一个完整的模块, 会报错, 所以需要动态引入一个组件
```
- vue为什么可以在不注册keep-alive的情况下直接使用keep-alive?
```
  vue在初始化组件时, 会先进行资源合并, keepAlive在vue初始化时已经加载到了option里, 组件初始化时会将components的原型指向option里的components
```
- vue是怎么做到监听数组变化?
``` javascript
  // 更改原方法
  // 示例

  Array.proptotype._push = function() {
    const result = this.push.apply(this, arguments)
    .... // 处理多余逻辑
    return result
  }
```
- vue对于prop和data之间的监听是怎么样的?
```
  props: 浅度监听(shallow render), 做到数据驱动视图更新即可
  data: 深度监听, 对data数据进行递归监听
```
- vue是怎么规定props、methods、data之间命名空间的优先级?
```
  props > methods > data
```
- vue生命周期能否是数组形式?
```
  可以是数组形式

  vue内部会对以下三种方式进行处理
  1. function => [function]
  2. [f, f] => [f, f]
  3. @hook:lifecyle = function => vm.$emit('hook:' + hook)
```
- v-model究竟做了什么?
```
  v-model默认绑定一个value变量以及一个input事件

  目前版本支持手动更改变量名称和事件名称
```
- vue.extend和new vue的区别是什么?
```
  new vue会进行初始化操作, 生成了一些option等操作

  vue.extend会继承初始化后的资源
```
- vue computed与watch的区别是什么?
```
  computed:
    1.惰性函数, 只有依赖发生变化时才会执行
    2.可以使用get, set方法
  
  watch:
    1.监听变量发生变化就会执行
    2.支持异步操作
```
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