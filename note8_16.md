### 在wsl下可以直接编译c语言

1，新建hello.cpp文件

int main(int arg,char* argc[]){
	printf("Hello CMake! \n");
}

2,编译hello.cpp
gcc hello.cpp -o hell

3,执行hell
./hell

### linux常用命令

1，在windows下开启wsl
可以进入具体目录 eg：d盘src下 执行wsl.exe就可以开启wsl

2，mkdir src  新建aa文件夹

3，touch a.txt 新建a.txt文件

4，vi a.txt 打开a.txt文件，可以对其进行编辑 按下i开始编辑，按下推出esc，输入 :wq!保存并推出

5，echo 可以直接打开一个相当于记事本的窗口，并可进行上面操作

6，rm aa 删除aa 文件

7，mv aa.txt aa.md  把aa.txt 文件修改为aa.md
