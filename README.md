# 1.GO2 踢球版本项目操作指南

## 网络连接与测试
1. 将网线插入板卡，ping 测试地址 `192.168.123.161`：
   - 如果 ping 不通或网线口未亮，检查网线或网络配置。
   - 详情参考宇树文档中心：[快速入门](https://support.unitree.com/home/zh/developer/Quick_start)。

## 工作空间配置
2. 进入工作空间（ws）后，运行以下命令：
   ```bash
   source devel/setup.bash
   ```
   - **注意**：每次打开新窗口都需要执行此命令。
   - 如果使用 `tab` 补全无索引，可通过此步骤定位问题。

## 启动与运行
3. 启动 ROS 核心服务：
   ```bash
   roscore
   ```

4. 运行 ROS 节点（根据提示确定是否需要 `eth0` 参数）：
   ```bash
   rosrun GO2_tasks go2_getinfo eth0
   ```
   - **说明**：之前编写的踢球 `police` 功能均可正常使用。
