## 5.2 - 5.8

项目上线

## 5.9 - 5.15

### 无值判断

1、解构赋值

```
const { result = [], message } = request
// 若设置默认值只对 undefined 对象生效，null 返回 null，NaN 返回 NaN
```
嵌套对象解构时，如果解构的外层对象为null或undefined会报错，其他情况都为找不到返回 undefined：
```
const { result:{res}, message=10 } = {result:null, message:undefined}
console.log(res, message) // res报错

const { result:{res}, message=10 } = {result:undefined, message:undefined}
console.log(res, message) // res报错

const { result:{res}, message=10 } = {result:NaN, message:undefined}
console.log(res, message) // undefined，10
```
2、&&

3、三元运算符

4、if
### 面临多个判断选择
####  策略模式
#### if + return
#### else if

### sticky粘性定位