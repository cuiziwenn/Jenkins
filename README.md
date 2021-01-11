# Jenkins
#### 什么是Jenkins
* Jenkins是一个开源的、提供友好操作界面的持续集成（CI）工具，起源于Hudson（Hudson是商用版），主要用于持续、自动的构建/测试软件项目、监控外部任务的运行（这个比较抽象，暂且写上，不做解释）。Jenkins用JAVA语言编写，可在Tomcat等流行的servlet容器中运行，也可以独立运行，通常与版本管理工具（SCM）、构建工具结合使用：常用的版本控制工具有SVN、GIT，构建工具有Maven、Ant、Gradle
#### 安装Jenkins
* 安装JAVA环境
    yum install java
* 查看当前JAVA版本
    java -version
* 添加Jenkins源
```
wget -O /etc/yum.repos.d/jenkins.repo http://jenkins-ci.org/redhat/jenkins.repo
rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
yum install jenkins
``` 
#### Jenkins配置
* JENKINS_HOME
JENKINS_HOME是Jenkins的主目录，jenkins工作的目录都在这里，包括Jenkins储存文件的地址、Jenkins的插件，生成的文件都在此目录下
```
<pre class="md-fences md-end-block" lang="shell" contenteditable="false" cid="n105" mdtype="fences" style="box-sizing: border-box; overflow: visible; font-family: Consolas, &quot;Liberation Mono&quot;, Courier, monospace; font-size: 0.9em; white-space: pre; display: block; break-inside: avoid; text-align: left; background: var(--code-block-bg-color); background-color: rgb(248, 248, 248); position: relative !important; border: 1px solid rgb(221, 221, 221); border-top-left-radius: 3px; border-top-right-radius: 3px; border-bottom-right-radius: 3px; border-bottom-left-radius: 3px; padding: 8px 1em 6px; margin-bottom: 15px; margin-top: 15px; width: inherit; color: rgb(51, 51, 51); font-style: normal; font-variant-caps: normal; font-weight: normal; letter-spacing: normal; orphans: auto; text-indent: 0px; text-transform: none; widows: auto; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">## Path:    Development/Jenkins
## Description: Jenkins Continuous Integration Server
## Type:    string
## Default:   "/var/lib/jenkins"
## ServiceRestart: jenkins
#
# Directory where Jenkins store its configuration and working
# files (checkouts, build reports, artifacts, ...).
#
JENKINS_HOME="/var/lib/jenkins"</pre>
```
* JENKINS_USER
JENKINS_USER是Jenkins的用户，拥有$JENKINS_HOME以及/var/log/jenkins的权限
```
<pre class="md-fences md-end-block" lang="shell" contenteditable="false" cid="n108" mdtype="fences" style="box-sizing: border-box; overflow: visible; font-family: Consolas, &quot;Liberation Mono&quot;, Courier, monospace; font-size: 0.9em; white-space: pre; display: block; break-inside: avoid; text-align: left; background: var(--code-block-bg-color); background-color: rgb(248, 248, 248); position: relative !important; border: 1px solid rgb(221, 221, 221); border-top-left-radius: 3px; border-top-right-radius: 3px; border-bottom-right-radius: 3px; border-bottom-left-radius: 3px; padding: 8px 1em 6px; margin-bottom: 15px; margin-top: 15px; width: inherit; color: rgb(51, 51, 51); font-style: normal; font-variant-caps: normal; font-weight: normal; letter-spacing: normal; orphans: auto; text-indent: 0px; text-transform: none; widows: auto; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">## Type:    string
## Default:   "jenkins"
## ServiceRestart: jenkins
#
# Unix user account that runs the Jenkins daemon
# Be careful when you change this, as you need to update
# permissions of $JENKINS_HOME and /var/log/jenkins.
#
JENKINS_USER="jenkins"</pre>
```
* JENKINS_PORT是Jenkins的端口，默认端口为8080
```
<pre class="md-fences md-end-block" lang="shell" contenteditable="false" cid="n111" mdtype="fences" style="box-sizing: border-box; overflow: visible; font-family: Consolas, &quot;Liberation Mono&quot;, Courier, monospace; font-size: 0.9em; white-space: pre; display: block; break-inside: avoid; text-align: left; background: var(--code-block-bg-color); background-color: rgb(248, 248, 248); position: relative !important; border: 1px solid rgb(221, 221, 221); border-top-left-radius: 3px; border-top-right-radius: 3px; border-bottom-right-radius: 3px; border-bottom-left-radius: 3px; padding: 8px 1em 6px; margin-bottom: 15px; margin-top: 15px; width: inherit; color: rgb(51, 51, 51); font-style: normal; font-variant-caps: normal; font-weight: normal; letter-spacing: normal; orphans: auto; text-indent: 0px; text-transform: none; widows: auto; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">## Type:    integer(0:65535)
## Default:   8080
## ServiceRestart: jenkins
#
# Port Jenkins is listening on.
# Set to -1 to disable
#
JENKINS_PORT="8080"</pre>
```
