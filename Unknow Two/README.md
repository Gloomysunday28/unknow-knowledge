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

![Unicode](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow%20Two/unicode.png 'Unicode')


### FontClass
> 优点
```
  1. 支持性好, 兼容到IE6
  2. 能够动态支持调整图标的大小, 颜色等等
  3. 可以无需引入iconfont到项目内, 直接使用动态链接
```
![FontClass](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow%20Two/fontclass.png 'FontClass')

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

![在线链接](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow%20Two/font-class-one.png '在线链接')
![对应类名](https://github.com/Gloomysunday28/unknow-knowledge/blob/master/Unknow%20Two/font-class-two.png '对应类名')



