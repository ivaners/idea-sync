# idea Settings Repository

**配置 Settings Repository**
如果要共享 IDE 设置，请执行以下步骤：

1. 在任何托管服务上创建 Git 存储库，例如 Bitbucket 或 GitHub。
2. 在安装了要共享其设置的 IntelliJ IDEA 实例的计算机上，导航到 File | Settings Repository。指定创建的远程仓库的 URL，然后点击 Overwrite Remote。
3. 在要应用设置的每台计算机上，在 Settings/Preferences dialog 对话框中，展开 Tools 节点并选择 Settings Repository，指定创建的远程仓库的 URL，然后点击 Overwrite Local。
   如果想要储存库保留远程设置和本地设置的组合，可以点击 Merge。如果检测到任何冲突，将显示一个对话框，可以在其中解决这些冲突。如果要使用本地设置覆盖远程设置，请单击点击 Overwrite Remote。

每次执行 **Update Project** 或 **Push** 操作时，或者当关闭项目或退出 IntelliJ IDEA 时，计算机的本地设置将自动与远程仓库中的设置同步。



在第一次同步时，系统将提示您指定用户名和密码。建议使用 [access token](https://link.juejin.im?target=https%3A%2F%2Fhelp.github.com%2Farticles%2Fcreating-a-personal-access-token-for-the-command-line%2F) 进行 GitHub 身份验证。如果由于某种原因，您想要使用用户名和密码而不是 access token，或者您的 Git 托管服务提供商不支持它，建议您配置 [Git credentials helper](https://link.juejin.im?target=https%3A%2F%2Fhelp.github.com%2Farticles%2Fcaching-your-github-password-in-git%2F)。



**idea settings repository can't be established错误解决**

原因是因为git的秘钥已经失效，可以通过配置~/.ssh/config增加配置来实现

idea setting repository保存的git配置文件位置是：

`D:\.IntelliJIdea2018.1\config\settingsRepository\repository\.git`

所以本身的git是没有问题的，只需要增加ssh会话即可

```
Host git@gitee.com
 HostName %h
 User huaiao
 IdentityFile C:/Users/Administrator/.ssh/id_rsa
 IdentitiesOnly yes
```

**Idea Edit Custom Vm options**

```
# custom IntelliJ IDEA VM options

-Xms512m
-Xmx1500m
-XX:ReservedCodeCacheSize=500m
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=0
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-javaagent:D:/Program Files/JetBrains/IntelliJ IDEA 2018.1.4/bin/JetbrainsCrack-2.10-release-enc.jar
```

