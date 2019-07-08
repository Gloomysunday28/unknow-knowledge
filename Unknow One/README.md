# IntersectionObserver

## 定义
```
  浏览器原生API, 用于自动观察目标元素是否在可视区域内, 被称为交叉观察器
```
> 实际用处
- 进入可视区域
![进入可视区域](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow%20One/enter.png '进入可视区域')
- 退出可视区域
![退出可视区域](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow%20One/leave.png '退出可视区域')

### 项目地址
[项目地址](https://gloomysunday28.github.io/unknow-knowledge/Unknow%20One/Intersectionobserver.html)

### 简介
```
优化点:
  不需要像getBoundingRect()那样去实时监听元素, 并且具有大量计算在里面
缺点:
  优先级很低, 只有线程闲下来才会执行, 通常是在requestIdleCallback里使用
```
> requestIdleCallback: 等待线程全部空闲下来才执行

写法:
const io = new IntersectionObserver(callback, option)
io.observer(el)
```
callback: entries -> 被观察的元素们, 是个数组
  entries:
  boundingClientRect: 与getBoundingRect参数一致
  intersectionRatio: 大于0就是进入了可视区域, 小于等于0就是离开可视区域
  intersectionRect: 与边界的交叉参数
  isIntersecting: 是否进入可视区域
  rootBounds: 描述与交叉区域观察者之间的交叉参数
  target: 观察元素
  time: 记录元素与交叉区域之间的时间

options:
  root: viewport, 可视区域的元素，
  rootMargin: 规定了可视区域的margin值, 可放大区域
  threshold: [], 规定了什么时候触发回调函数, 参数列表可以是[0, .25, .5, .075, 1]
```

:sparkles:
## 关注我~ 每天告诉你一个小技巧