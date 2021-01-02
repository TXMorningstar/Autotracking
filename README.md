# Autotrack自动寻路模块

---

# 简介
**Autotrack**是一个用**python**编写的，非常简单的自动寻路模块  
只能对二维坐标寻路，并且不能走斜线  
将此模块放入你的程序目录里，用import导入即可使用  
在编写时我尽可能地写了完整的注释，使用起来应该不会很麻烦  
代码写的很乱，不过看不懂也没关系，能用就行

## 创作动机
在我们制作的Galgame(名字未定)中，需要大量使用到自动寻路功能。为了方便制作，我决定把一些复杂的方法打包起来做成模块方便反复调用。  
看了一下网上的各种算法，最终打算采用A*算法  
已经尽我所能地把这个模块做到最好了（尽可能的简单且高效），不过由于个人能力不足……应该并不是最佳的方案，总之如果你觉得代码还能看得过去的话随便拿去用就是了

---

# 说明书：
**安装**  
Autotrack模块的核心是modules文件夹里的autotrack.py  
把autotrack.py下载到你的程序目录里，然后在你的脚本中使用`from autotrack import *`  
导入后，你需要为它创建一个实例对象，然后传入地图的长和宽  
例：`a = AStarTrack(16,16) #创建一个16x16的地图用于寻路`  
或：`a = BestFirstTrack(16,16) #这个类的寻路速度更快一些，但精准度不如AStarTrack`
>如果你需要在cmd窗口调试它，可以再向其中传入一个字符串  
>`"map"`把寻路的每一步都以一个便于阅读的方式打印到cmd窗口上）  
>`"raw"`把寻路中每一个节点内的详细数据都打印出来方便查看，格式为`(F,G,H),(父节点x,父节点y)`  
>例：`a = AStarTrack(16,16,"map")`

随后，利用AStarTrack类的方法进行寻路  
如果实在看不懂的话就参考一下main.py里的示范

**放置障碍**  
`obstacle(x,y)`  
例：`a.obstacle(5,5)`  
在(x,y)的位置放置一个障碍  
将障碍部署进地形后在自动寻路时会绕开障碍进行寻路

**寻路**  
`target(start,end)`  
例：`a.target((1,1),(3,3))`  
start和end应为两个元组，元组内记录x,y的值  
返回值为一个元组，元组内记录了从起点到终点每一步所对应的坐标，以列表的形式返回，例：`[(1,2),(1,3),(2,3)]`


**打印地图**  
`printMap()`  
将地图打印到cmd窗口上  
在debug时可以用这个功能检查程序哪里出了问题

**打印地图数据**  
`printRawMap()`  
将地图的每一个格子内的数据都打印到cmd窗口里

---

<p align="right">
作者：天选之人<br/>
项目创建时间：2020/12/25
</p>
