# GO2强化学习流程部署启动方式

### 1.先cd技进入go2_ws文件夹

### 2.重新开一个终端source后，启动gait obs节点
```
source devel/setup.sh
rosrun GO2_tasks go2_getgaitobs eth0
```
 - 新开一个终端可以查看该节点输出的信息
```
source devel/setup.sh
rostopic list //查看当前所有的rose node
rostopic echo /gait_observation  //查看gait obs node output
```
 - 注意，每次开启新的终端需要使用ros相关功能都需要source一下，别忘记！！
### 3.启动lowlevel模式，并且初始化站姿势
 在这个模式中启动会自动切换到低级控制中，手柄将不可用，如要手柄控制，请使用ros启动state client文件（自动切换两种模式，从高级到低级也可以用这个）
```
rosrun GO2_tasks go2_lowcmd_init eth0 //初始化站姿
rosrun GO2_tasks go2_robot_state eth0 //切换模式，单次切换，可从高到低也可从低到高
```

### 4.启动推理
在另一个文件夹中的go2_sim2real存放了ros版本的推理文件
```
rosrun go2_sim2real play_fake.py
```
然后就会接受ros并且进行推理/发布action
