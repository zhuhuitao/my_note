在 Linux 中使用 VSCode 连接并使用 libusb，你需要确保 libusb 库已经安装，并且在编译时正确链接到你的项目。以下是详细步骤：

1. 安装 libusb
首先，确保 libusb 库已经安装在你的系统中。你可以使用包管理器安装它：

bash
sudo apt-get update
sudo apt-get install libusb-1.0-0-dev
2. 配置 VSCode
在 VSCode 中，你需要配置编译任务来编译你的代码。以下是如何设置：

a. 创建 tasks.json 文件
打开 VSCode。
点击左侧的“运行和调试”图标。
点击左上角的齿轮图标，选择“创建 launch.json 文件”。
选择你的环境（例如 C++）。
在 .vscode 文件夹中创建一个 tasks.json 文件，配置如下：
json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build libusb project",
            "type": "shell",
            "command": "g++",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}",
                "-lusb-1.0"
            ],
            "options": {
                "cwd": "${workspaceFolder}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "detail": "生成的命令：${command} ${args}"
        }
    ]
}
这个配置定义了一个任务，用于编译当前打开的 C++ 文件，并链接 libusb 库。

b. 编译项目
打开你的 C++ 文件。
按下 Ctrl+Shift+B 或从菜单中选择“终端”>“运行任务”。
选择“build libusb project”任务。
3. 包含 libusb 头文件
在你的 C++ 源文件中，确保正确包含 libusb 头文件：

cpp
#include <libusb-1.0/libusb.h>
4. 编写代码
编写你的代码，使用 libusb 库的功能。例如，初始化 libusb、查找设备等。

5. 调试（可选）
如果你需要调试你的代码，你可以在 launch.json 中配置调试器。这将允许你设置断点并逐步执行代码。

6. 运行和测试
编译并运行你的程序，检查是否能够正确使用 libusb 库。

通过这些步骤，你应该能够在 VSCode 中配置和使用 libusb 库。如果遇到任何问题，请检查你的编译命令和链接选项，确保 libusb 库已正确安装并链接到你的项目。