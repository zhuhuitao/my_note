在本地 Maven 仓库中，.arr.sha1 和 .pom.sha1 文件通常用于存储对应文件的 SHA1 校验值，用于验证文件的完整性和一致性。以下是获取这些值的方法：

打开命令行工具，切换到包含 .jar 或 .pom 文件的目录。
使用以下命令生成 SHA1 校验值，并将其保存到对应的 .sha1 文件中：
CertUtil -hashfile <文件名> SHA1 > <文件名>.sha1

CertUtil -hashfile lib_account_authenticator-1.0.7.aar SHA1 > account-authenticator-1.0.7.aar.sha1

 CertUtil -hashfile account-authenticator-1.0.7.pom SHA1 > account-authenticator-1.0.7.pom.sha1