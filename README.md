# idea Settings Repository

**Idea Terminal配置**
```
<option name="myShellPath" value="/bin/bash" />
<option name="myShellPath" value="C:\Windows\System32\cmd.exe" />
```

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
-Xms2500m
-Xmx3000m
-XX:ReservedCodeCacheSize=0m
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-XX:CICompilerCount=2
-Dsun.io.useCanonPrefixCache=false
-Djava.net.preferIPv4Stack=true
-Djdk.http.auth.tunneling.disabledSchemes=""
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-Dkotlinx.coroutines.debug=off
-Djdk.module.illegalAccess.silent=true
-Dide.no.platform.update=true
-javaagent:C:\jetbrains-agent.jar
# 设置编码
-Dfile.encoding=UTF-8
# 设置抗锯齿
-Dawt.useSystemAAFontSettings=on
-Dide.run.dashboard=true
-Djdk.attach.allowAttachSelf=true
-Didea.plugins.path=C:/Users/Administrator/AppData/Local/JetBrains/Toolbox/apps/IDEA-U/ch-0/193.5662.53.plugins
```

