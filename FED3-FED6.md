FED3 dom节点查找
------
> 描述
> 查找两个节点的最近的一个共同父节点，可以包括节点自身
> 输入描述：
> oNode1 和 oNode2 在同一文档中，且不会为相同的节点

    function commonParentNode(oNode1, oNode2) {
        for(; oNode1; oNode1 = oNode1.parentNode) {
            if (oNode1.contains(oNode2)) {
                return oNode1
            }
        }
    }


FED4 根据包名，在指定空间中创建对象
------
> 描述
> 根据包名，在指定空间中创建对象
> 输入描述：
> namespace({a: {test: 1, b: 2}}, 'a.b.c.d')
> 输出描述：
> {a: {test: 1, b: {c: {d: {}}}}}

    function isObject(value) {
      return Object.prototype.toString.call(value).slice(8, -1) === 'Object'
    }
    function namespace(oNamespace, sPackage) {
      let strArr = sPackage.split('.')
      let res = oNamespace
      for (let i = 0; i < strArr.length; i++) {
        let packageName = strArr[i]
        if (!oNamespace.hasOwnProperty(packageName) || !isObject(oNamespace[packageName])) {
          oNamespace[packageName] = {}
        }
        oNamespace = oNamespace[packageName]
      }
      return res
    }
    let result = namespace({a: {test: 1, b: 2}}, 'a.b.c.d')
    console.log(result)

FED5 数组去重
------
> 描述:
> 为 Array 对象添加一个去除重复项的方法
> 输入：[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a', 'a', NaN]
> 输出：[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a']

    // 方法一
    Array.prototype.uniq = function () {
      // 定义常量 res,值为一个Map对象实例
      // 如果res中存在该键就返回false过滤数组中的对象
      // 否则向res中添加一个值为1的新键且返回该res对象, 不进行数组过滤  
      // 返回arr数组过滤后的结果，结果为一个数组
      const res = new Map();
      return this.filter((a) => !res.has(a) && res.set(a, 1))
    }

    // 方法二
    Array.prototype.uniq = function () {
      let arrToSet = new Set(this)
      return Array.from(arrToSet)
    }

    // 方法三
    Array.prototype.uniq = function ()  {
      let newArr = []
      let flag = 0
      for(let i = 0; i < this.length; i++) {
        if(Number.isNaN(this[i]) && flag === 0) {
          newArr.push(this[i])
          flag++
        } else if (this.indexOf(this[i]) === i) {
          newArr.push(this[i])
        }
      }
      return newArr
    }

    console.log([true, false, null, undefined, NaN, 0, 1, {}, {}, 'a', 'a', NaN].uniq())

FED6 斐波那契数列
------
    // 方法一
    function fibonacci(n) {
      if (n <= 2) {
        return 1
      } else {
        return fibonacci(n-1) + fibonacci(n-2)
      }
    }

    // 方法二
    function fibonacci(n) {
      let a = 0, b = 1, arr = [0, 1]
      while (arr.length < n + 1) {
        [a, b] = [b, a + b]
        arr.push(b)
      }
      return arr[arr.length - 1]
    }
    
    // 方法三
    function fibonacci(n) {
      if (n <= 2) {
        return 1
      }
      let f1 = f2 = 1, temp
      for (let i = 2; i < n; i++) {
        temp = f1
        f1 = f2
        f2 = temp + f2
      }
      return f2
    }

    console.log(fibonacci(8)) //21



    
