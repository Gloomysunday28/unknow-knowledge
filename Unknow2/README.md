# 你不知道的iconfont

## icon共有3种使用方法
### Unicode
> 优点
```
  1. 支持性好, 兼容到IE6
  2. 能够动态支持调整图标的大小, 颜色等等
```
> 缺点
```
  1. 无法支持多颜色图标
  2. 在不同浏览器设备中显示的状态是不同的
```

> 使用方法
```
  1. 引入iconfont项目的iconfont.css, iconfont.svg, iconfont.ttf, iconfont.woff, iconfont.woff2, iconfont.eot
  2. 项目中使用, <i class="iconfont">unicode码</i>
```

![Unicode](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow2/unicode.png 'Unicode')


### FontClass
> 优点
```
  1. 支持性好, 兼容到IE6
  2. 能够动态支持调整图标的大小, 颜色等等
  3. 可以无需引入iconfont到项目内, 直接使用动态链接
```
![FontClass](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow2/fontclass.png 'FontClass')

> 缺点
```
  如果想要自定义名称 需要手动修改iconfont的名称
```

> 使用方法
```
  1. 引入在线链接 或者 按照unicode方法直接下载引入
  2. 寻找以下图对应的icon
  3. <i class="iconfont 对应的class"></i>
```

![在线链接](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow2/font-class-one.png '在线链接')
![对应类名](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow2/font-class-two.png '对应类名')


### Symbol svg-icon ( 逐渐成为主流技术 )
> 优点
```
  1. 矢量图, 伸缩不会失真
  2. 支持设置大小, 颜色
  3. 支持ie9+
  4. 可以利用css实现动画
  5. 减少http请求
  6. 可以精细控制SVG每一部分
  7. 支持多色图标
```
> 缺点
```
  生成js文件里会写入fill: currentColor样式, 开发者无法更改其颜色
  解决方案: 不使用color, 而是使用fill来更改颜色
```

> 说明
```
  symbol 不需要woff|eot|ttf|这些字体库, 只需要引入对应的js即可
```

> 使用方法
```
  1. 按照下图找到对应的类名
  2. <svg class="icon" aria-hidden="true">
      <use xlink:href="#对应类名"></use>
     </svg>
  3. 定义好icon的通用样式
```

![Symbol对应类名](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow2/symbol.png 'Symbol对应类名')

:sparkles:
## 关注我~ 每天告诉你一个小技巧