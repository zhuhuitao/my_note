# SytemSever

### startBootstrapServices(t);

startBootstrapServices 方法是包含在 SystemServer 类中的，它主要负责启动一些最基础的系统服务，这些服务在整个系统运行的早期阶段是必需的。以下是一些典型的 Bootstrap 服务及其作用：
Installer Service：

负责安装和更新应用程序及其组件。
DeviceIdentifierPolicyService：
用于管理设备标识符政策。
Activity Manager：

负责启动应用、管理进程、任务和内存。
处理应用生命周期和任务堆栈。
Power Manager：

管理设备的电源状态，如休眠、唤醒等。
提供电源控制政策以延长电池续航。
Package Manager：

负责管理应用包的安装、卸载、查询和权限等。
User Service：

管理用户，会话的服务，支持多用户模式。
Display Manager：

管理显示设备和显示模式。
控制屏幕亮度、旋转等显示相关操作。
Input Manager：

管理输入设备（如触摸屏、键盘等）和输入事件的分发。


### startCoreServices(t);
### startOtherServices(t);
### startApexServices(t);