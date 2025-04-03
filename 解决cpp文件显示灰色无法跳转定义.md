# 【解决 VSCode C++ symbol 灰色 / 无法跳转问题】

## 1. 修改 CMakeLists.txt
打开 src/GO2_tasks/CMakeLists.txt，末尾添加：

include_directories(
    ${catkin_INCLUDE_DIRS}
    ${PROJECT_SOURCE_DIR}/devel/include
    ${PROJECT_SOURCE_DIR}/build
)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

## 2. 重新编译，生成 compile_commands.json

cd ~/go2_ws
catkin_make clean
catkin_make

## 3. 在工作空间下创建 VSCode 配置文件
在 go2_ws/.vscode/ 目录下新建 c_cpp_properties.json，并写入：

cat > .vscode/c_cpp_properties.json << EOF
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "\${workspaceFolder}/**",
                "\${workspaceFolder}/devel/include",
                "\${workspaceFolder}/build/**"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/g++",
            "cStandard": "c11",
            "cppStandard": "c++14",
            "intelliSenseMode": "linux-gcc-x64",
            "compileCommands": "\${workspaceFolder}/build/compile_commands.json"
        }
    ],
    "version": 4
}
EOF

## 4. 安装 VSCode C/C++ 插件
通过 VSCode 扩展市场在远程环境下安装 Microsoft 官方 C/C++ 插件

## 5. VSCode 内刷新配置
在 VSCode 里执行：

按 Ctrl + Shift + P 输入：
C/C++: Rescan Workspace
CMake: Configure

## 6. 重启 VSCode

✅ 此时 Ctrl + 鼠标点击 将可以正常跳转 Unitree SDK 的 position() imu_state() 等接口
