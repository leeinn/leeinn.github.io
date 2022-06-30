---
title: node处理文件结构
date: 2022-06-07 14:55:56
tags:
excerpt: 一次switch截图引发的探索
---
switch截图在本机是按游戏文件夹分类 um很合理
但截图数超1k就必须上sd卡 um京东立马下单,不能影响我记录xb2
但导出的时候发现Album文件夹下怎么会有这么多日期子文件夹 
几千张截图就这么分散在几十个folder里??

belike:
```
Album
└── (Year)
    └── (Month)
        └── (Day)
            ├── 01.jpg
            ...
            └── 31.jpg


对比本机路径：
Album
├── xb2
|   ├── 01.jpg
|   └── 02.jpg 
├── mhxx
...
└── zelda
```
很离谱的嵌套千层饼 如果是31天就是31个文件夹的分散图片 就算想给截图手动按游戏分类 但在不解决folder层级前也是耗时很高的电子拧螺丝

好的现在目标明确了 **打平文件层级**
再倒推技术实现过程 打平层级 -> 移动所有文件 -> 递归获取所有文件路径 -> node fs模块

用到的fs模块：
- readdir 
- stat (子方法可以判断 文件or文件夹) 
- rename (修改路径名等价移动)

```js
const getFilePath = (curPath, func) => {
    fs.readdirSync(curPath).forEach( path => {
        const filePath = path.join(curPath, path)
        if( fs.statSync(filePath).isFile() ){
            func(filePath)
        }else{
            getFilePath(filePath, func)
        }
    })
}

const moveFile = (filePath) => {
    const fileName = filePath.split('/').pop()
    const myFolder = 'myPic'  // 新建的和js同级文件夹
    const newPath = `./${myFolder}/${fileName}`  
    
    fs.renameSync(filePath, newPath)
}

const run = () => {
    const path = './Album'
    getFilePath(path, (filePath)=>{
        moveFile(filePath)
    })
}

run()
```
done (但游戏分类还得靠自己)

当然也可以继续改造 获取shell中的参数 手动确定文件路径 再自动创建文件夹等
`process.argv` 的第三个及以后的值是输入的参数
```js
const [nodeEnv,dir,...args] = process.argv
```

# 延伸
那已经能拿到所有文件的路径了 还能做什么捏
我只能说有无限的可能
- 批量改名
- 批量删除
- ...

解放双手了bro