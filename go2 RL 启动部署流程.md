# GO2强化学习流程部署启动方式

## 1.先cd技进入go2_ws文件夹

## 2.重新开一个终端source后，启动gait obs节点
```
source devel/setup.sh
rostopic echo /gait_observation
```
新开一个终端可以查看该节点输出的信息
```
rostopic list //查看当前所有的rose node
rostopic echo /gait_observation  //查看gait obs node output
```
