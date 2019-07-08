# 你不知道的Node寻找文件路径

## 前言
```
  Node是使用Commonjs规范的一个独立于浏览器的运行环境, 内嵌V8引擎, 可以独立运行JS
  里面的模块系统是Node的重要模块
  下面来说下Node在引入模块时究竟是怎么去查找的
```

## 日常使用
> /path/to/require.js
``` javascript
  const otherModule = require('otherModule')
```

### 以上代码是怎么寻找到模块的?
```
  1. 首先确定该模块是否是核心模块? 是 ? 直接使用 : 跳到下一步
  2. 其次确定该模块是否是内置模块? 是 ? 直接使用 : 跳到下一步
  3. 第三方模块查找: Node设定了一个名为node_modules的文件夹来存储第三方模块
    (1). 寻找/path/to/node_modules/otherModule.js
    (2). 若没有找到, 则找寻/path/to下的otherModule文件夹, 找寻到后, 继续寻找package.json文件, 找不到, 则指向index.js
      [1]. 找到后, 首先寻找module字段, 若有, 则找到对应的文件, 若没有, 则寻找main字段
      [2]. main字段找到后, 找到对应的文件, 若没有, 则指向index.js
  4. 若以上都找不到, 则递归往上冒泡寻找, 直到最顶层, 找不到, 则报错
```

### 建议
```
  node_modules一般存放在项目的根目录下统一管理第三方插件
```

:sparkles:
## 关注我~ 每天告诉你一个小技巧
