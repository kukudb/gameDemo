# gameDemo
项目介绍：
项目是一款基于追逐的非平衡对抗的游戏，玩家可以自由选择扮演人类和怪兽在充满各种障碍和道具的地图上进行追逐游戏，到达终点后人类获得武器，并且等待救援的到来，在此期间
人类需要撑过怪物的攻击来获得胜利，反之怪物获胜。

该项目是由小组合作的，个人负责部分为：

1.负责玩家的移动：
使用navigation导航，烘焙网格并设置终点目标，实现玩家自动寻路的功能。
![image](https://github.com/kukudb/gameDemo/assets/134269517/a1203a84-f582-46cf-99a5-bd46195dcb14)

2.负责人类玩家动画状态机的设置，以及转换。主要有前后左右受力的翻滚，跑步，挂机等待，射击的动作。
![image](https://github.com/kukudb/gameDemo/assets/134269517/8c52c9e5-9864-46df-841e-faf9e2a85df4)

3.玩家自动射击功能的实现：
在玩家触发器碰撞体范围内搜寻带有怪兽标记的最近怪兽，从枪口到怪兽中点方向发射子弹实体，同时生成发射特效，碰到怪兽时生成打击特效。
![image](https://github.com/kukudb/gameDemo/assets/134269517/0ee26555-422b-4477-942b-461116036911)

4.用对象池优化玩家的射击：
玩家射击碰到怪兽后或者3s后，子弹可见性置为fasle。玩家发射子弹时，先令子弹的坐标等于枪口的坐标，再令子弹的可见性设置为true，子弹附带特效也同理。

5.负责摄像机系统的开发
使用cinemachine负责场景中不同摄像机的切换，镜头的振动效果。对各个事件设置优先级，优先级高会先执行，相同的事件会覆盖，不重要的事件如全屏分屏的镜头可能会饥饿。由于事件触发会剥夺摄像机，如果不加以限制，就会出现镜头切换太快的闪屏效果。考虑到这点使用协程队列管理触发摄像机切换的事件，一次只start一个协程。


全屏镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/4d1a5b14-358f-4d2a-91f3-d34f80db8faf" width="700px">


分屏镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/fc721435-2638-4654-a92a-f2e13a50894e" width="700px">


第一名镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/bc176a93-b334-49b8-a2db-fccb61aea2b8" width="700px">


最后一名镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/8a76348c-c0fd-4b3d-a910-1dd308c7dfb2" width="700px">


怪兽距离玩家很近的镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/a02d67fa-2a78-4c44-b884-b81a7c454905" width="700px">


玩家通过终点的镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/357601bc-822d-493a-8d3d-8718c7bdf53d" width="700px">


不是事件触发的镜头，只在开始和结束的固定的镜头。
开始镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/79280f2e-dfa0-4609-9ea4-e56d4211bccf" width="700px">


最终阶段镜头：

<img src="https://github.com/kukudb/gameDemo/assets/134269517/3e8c1332-0faa-4ffb-9cd7-de26f7388ee0" width="700px">

6.各种道具的实现：利用协程来控制各个效果时间
眩晕道具：碰撞体碰到玩家后改变人类动画状态机到眩晕状态

![image](https://github.com/kukudb/gameDemo/assets/134269517/1bb69cc6-d93f-4b0e-9dde-f81eaed348f1)
![image](https://github.com/kukudb/gameDemo/assets/134269517/259a0e8b-36d3-4641-94b0-d46076cc2497)

紊乱道具：改变玩家的navigation 的目标地点，让人类玩家往回走

![image](https://github.com/kukudb/gameDemo/assets/134269517/e9c113a9-8547-4908-8a3f-e3717dbd3ccf)
![image](https://github.com/kukudb/gameDemo/assets/134269517/a469ae56-f0ed-46de-84e1-7c8ce4bfed4c)

护盾道具：一段时间内怪兽不能抓捕人类

![image](https://github.com/kukudb/gameDemo/assets/134269517/40ea1946-4313-4a14-88db-b165a4dfa950)
![image](https://github.com/kukudb/gameDemo/assets/134269517/c44f22ab-c954-4d0e-b5a3-c540eabacd00)


还有加速道具、攻击翻倍的道具、攻速翻倍的道具等等不一 一展示。

7.负责武器获取时、道具使用时、通过终点时的播报，不具有时效性，塞入队列播报即可

![image](https://github.com/kukudb/gameDemo/assets/134269517/85dceb84-f348-4da7-8569-2ccfcb5c38b1)

![image](https://github.com/kukudb/gameDemo/assets/134269517/47233523-c0e4-437d-98d7-2d1b57319a57)

![image](https://github.com/kukudb/gameDemo/assets/134269517/3acab91c-99f1-48c8-99f1-e12d7857f525)

8.负责游戏测试以及bug的修复。

最后，游戏demo视频


https://github.com/kukudb/gameDemo/assets/134269517/59228652-3352-4574-b02d-ccfd8173b15a


<video src="https://raw.githubusercontent.com/kukudb/gameDemo/main/b.mp4" controls="controls">
您的浏览器不支持 video 标签。
</video>
画质较高的视频：
https://raw.githubusercontent.com/kukudb/gameDemo/main/a.mp4
