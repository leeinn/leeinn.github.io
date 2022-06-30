最近进blog经常会有布局混乱，查network发现主题相关的各种cdn全挂了  
原生配置中默认把资源都挂载在 jsdelivr 上  
但但21年底备案被吊销，官方issue被轰炸在修在修hhh  
原来是自己电脑一直挂梯子所以没有发现吗hhh  
本来想自己扔到对象存储但文件数太多有点繁琐   
加个todo 后续可以用 `node + shelljs` 批量下载一波文件

暂时的替代方案：[unpkg](https://www.cnblogs.com/lujiahao/p/15710931.html)