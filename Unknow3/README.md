# 箭头函数

## Es6 新语法, 使用 (=>) 来定义函数

> 写法:
``` javascript
  const arrow = x => y
  const arrows = x => {
    return y
  }
```
<code>如果没有花括号, 则表示y就是返回值, 可以使用()</code>

## 特性
```
  1. 箭头函数的this指向与普通函数不同(下面会详细说明)
  2. 箭头函数里面不具备arguments变量
  3. 箭头函数不具备原型链, 也就不具备constructor构造器, 无法使用new
  4. 箭头函数无法成为生成器(generator)
```

## This指向说明
> 普通函数(执行时才会定义this指向)
```
  1. 处在上下文里, this指向上下文
    exp: 
      const obj = {
        says() {
          return this
        }
      }
    this指向obj
  
  2. 使用call, apply, bind方法, this指向指定的变量
  3. new函数, this指向实例
  4. 没有任何操作, this指向windows, 严格模式下, this指向的是Undefined
```

> 箭头函数
```
  this指向父级执行上下文
  1. exp:
      const obj = {
        says: () => {
          return this
        }
      }

    this指向的是windows, says的父级是obj,而obj处于windows的执行上下文, 所以this指向windows
```

> 题测
``` javascript
    const obj = {
      says() {
        setTimeout(() => {
          return this
        }, 0)
        setTimeout(function() {
          return this
        }, 0)
      }
    }
```

<code>上面的this分别指向谁？</code>

:sparkles:
## 关注我~ 每天告诉你一个小技巧
