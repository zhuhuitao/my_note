1,解包APK文件： 在命令提示符或终端窗口中，导航到包含APK文件的目录，然后运行以下命令： 删除签名文件： 删除解包目录中的签名文件（通常位于 META-INF 文件夹下）：
java -jar .\apktool.jar d yourapp.apk -o output_directory
运行上面的命令会把apk解压到output_directory中，我们可以手动进入文件夹删除META-INF文件

2，重新打包apk
java -jar .\apktool.jar b decoded_apk -o app-release-unsigned.apk

3,重新签名
 jarsigner -verbose -keystore p6.keystore -signedjar signed.apk app-release-unsigned.apk platform




