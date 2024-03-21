# gameDemo
项目介绍：
项目是一款基于追逐的非平衡对抗的游戏，玩家可以自由选择扮演人类和怪兽在充满各种障碍和道具的地图上进行追逐游戏，到达终点后人类获得武器，并且等待救援的到来，在此期间
人类需要撑过怪物的攻击来获得胜利，反之怪物获胜。

个人负责部分：

1.负责玩家的移动：
使用navigation导航，烘焙网格并设置终点目标，实现玩家自动寻路的功能。
![image](https://github.com/kukudb/gameDemo/assets/134269517/a1203a84-f582-46cf-99a5-bd46195dcb14)
<img src="https://github.com/kukudb/gameDemo/assets/134269517/a1203a84-f582-46cf-99a5-bd46195dcb14" width="210px">

2.负责摄像机系统的开发
使用cinemachine负责场景中不同摄像机的切换。对各个事件设置优先级，优先级高会先执行，相同的事件会覆盖，不重要的事件如全屏分屏的镜头可能会饥饿。由于事件触发会剥夺摄像机，如果不加以限制，就会出现镜头切换太快的闪屏效果。考虑到这点使用协程队列管理触发摄像机切换的事件，一次只start一个协程。


全屏镜头：

![image](https://github.com/kukudb/gameDemo/assets/134269517/4d1a5b14-358f-4d2a-91f3-d34f80db8faf)

分屏镜头：

![image](https://github.com/kukudb/gameDemo/assets/134269517/fc721435-2638-4654-a92a-f2e13a50894e)

第一名镜头：

![image](https://github.com/kukudb/gameDemo/assets/134269517/bc176a93-b334-49b8-a2db-fccb61aea2b8)

最后一名镜头：

![image](https://github.com/kukudb/gameDemo/assets/134269517/8a76348c-c0fd-4b3d-a910-1dd308c7dfb2)

怪兽距离玩家很近的镜头：
![1711017380670](https://github.com/kukudb/gameDemo/assets/134269517/a02d67fa-2a78-4c44-b884-b81a7c454905)


玩家通过终点的镜头：
![image](https://github.com/kukudb/gameDemo/assets/134269517/357601bc-822d-493a-8d3d-8718c7bdf53d)

不是事件触发的镜头，只在开始和结束的固定的镜头：
开始镜头：

结束镜头：
