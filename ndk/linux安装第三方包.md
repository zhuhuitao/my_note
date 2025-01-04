在 WSL 中编译 libusb 的步骤如下：

安装依赖：
在编译 libusb 之前，需要安装一些必要的依赖包。这些依赖包通常包括 build-essential（包含基本的编译工具链），autoconf、automake、libtool（用于自动生成 configure 脚本和 Makefile），以及 libudev-dev（用于udev设备的支持）。你可以使用以下命令安装这些依赖：

bash
sudo apt-get update
sudo apt-get install build-essential autoconf libtool libudev-dev

获取 libusb 源码：
你可以从 libusb 的官方网站或 GitHub 仓库下载最新的源码。以 GitHub 为例，可以使用以下命令克隆仓库：

bash
git clone https://github.com/libusb/libusb.git

编译 libusb：
进入源码目录，并执行以下步骤进行编译：

运行 autogen.sh 脚本生成 configure 文件：
bash
cd libusb
./autogen.sh
运行 configure 配置项目生成 Makefile：
bash
./configure
运行 make 进行编译：
bash
make
运行 make install 进行安装，这会将 libusb 安装到系统中：
bash
sudo make install

验证安装：
安装完成后，你可以通过以下命令验证 libusb 是否成功安装：

bash
pkg-config --modversion libusb-1.0
如果输出显示了 libusb 的版本号，则说明安装成功。