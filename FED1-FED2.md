FED1 修改this指向
-------
> 封装函数 f，使 f 的 this 指向指定的对象

题解: https://blog.csdn.net/jiang7701037/article/details/99975245

    function bindThis(f, oTarget) {
      // 如果直接运行bindThis，就不用返回函数，直接返回运行结果，传递的参数获取oTarget之后的参数。
      return function() { 
        // 获取传递的参数并转换成数组
        let args = Array.prototype.slice.call(arguments)
        return f.apply(oTarget, args)
      }
    }
    let f = bindThis(f, oTarget);
    f(args);

FED2 获取url参数
 -------
 > 1.指定参数名称，返回该参数的值 或者 空字符串
 > 2.不指定参数名称，返回全部的参数对象 或者 {}
 > 3.如果存在多个同名参数，则返回数组
 > 4.不支持URLSearchParams方法
 >>     示例：
 >>     输入：'http://www.nowcoder.com?key=1&key=2&key=3&test=4#hehe', 'key'   
 >>     输出：[1, 2, 3]  

    function getUrlParam(sUrl, sKey) {
      let urlParam = {}
      let startIndex = sUrl.indexOf('?')
      if (startIndex === -1) {
        urlParam = sKey ? '' : {}
        return urlParam
      }
      let paramStr = sUrl.slice(startIndex + 1, sUrl.length).split('#')[0].split('&') // 获取参数字符串
      for (let i of paramStr) {
        let res = i.split('=')
        if (urlParam[res[0]] && urlParam[res[0]] instanceof Array) {
          urlParam[res[0]].push(res[1])
        } else if (urlParam[res[0]]) {
          urlParam[res[0]] = [urlParam[res[0]], res[1]]
        } else {
          urlParam[res[0]] = res[1]
        }
      }
      if (sKey) {
        return urlParam[sKey] ? urlParam[sKey] : ''
      } else {
        return urlParam
      }
    }
    let result = getUrlParam('http://www.nowcoder.com?key=1&key=2&key=3&test1=4#hehe', 'key')
    console.log(result)
