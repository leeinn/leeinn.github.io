---
title: 手写
date: 2022-03-29 15:40:17
excerpt: 顾名思义 就是用手写的
index_img: img/default.png
---
# 快排
1. 在数据集之中，选择一个元素作为"基准"（pivot）。
2. 所有小于"基准"的元素，都移到"基准"的左边；所有大于"基准"的元素，都移到"基准"的右边。3. 对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素为止。
```js
var quickSort = function(arr){
  if(arr.length <= 1) return arr

  let pivot = arr.splice(0,1)[0]
  let left = []
  let right = [] 

  for(let i of arr){
    if(i < pivot){
      left.push(i)
    }else{
      right.push(i)
    }
  }

  return [...quickSort(left), pivot, ...quickSort(right)]
}
```

# Promise.all
传入一个数组 数组每一项promise都执行完后 才可以继续执行后续.then 成功返回每个promise结果的数组，某项reject时直接返回该项的状态值（失败）
all用来处理多个异步，belike一个页面上需要有多个ajax同时请求到后才正常显示 之前都使用loading 

因为可以调用.then 所以all方法返回的也是一个promise对象 只是resolve()的时机由数组中的promise对象控制 

给每项promise对象手动加then
```js
Promise.myAll = function(arr){
  var len = arr.len
  var resolveRes = []

  return new Promise((resolve, reject) => {
    for(let i of arr){
      i.then(res => {
        resolveRes.push(res)
      
      if(resolveRes.length === len){
          resolve(resolveRes)
        }
      }).catch(err => {
        return reject(err)
      })
    }
  })  
}
```

# 