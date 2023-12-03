# Git学习





## 第一章、git简介



### 1.1 git安装

* **windows安装**

  https://www.cnblogs.com/wlming/p/12213876.html 

  1. 开始安装

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232150712.png" alt="image-20231121232150712" style="zoom:50%;" />

  2. 下面默认设置就行:下图(下一步) ，这个的下一步也使用默认 直接下一步

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232201863.png" alt="image-20231121232201863" style="zoom:50%;" />

  3. **选择默认的文本编辑器**

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232234705.png" alt="image-20231121232234705" style="zoom:50%;" />

  4. 然后修改环境变量(选第一完全不修改)

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232250370.png" alt="image-20231121232250370" style="zoom:50%;" />

  5. 选择客服端**本地库和远程库连接方式**(1通用连接2使用Windows连接方式)

* <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232456050.png" alt="image-20231121232456050" style="zoom:50%;" />

  6. **选择换行符的方式**(**1**检查文件时LF 转为 CRLF 提交相反)

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232521731.png" alt="image-20231121232521731" style="zoom:50%;" />

  7. **选择终端**(1Git默认终端(是liunx命令)2选择Windows终端(wind命令))

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232541546.png" alt="image-20231121232541546" style="zoom:50%;" />

  8. 使用默认(选择第二个需要安装.NET framework c4.5.1以上版本)

     NET framework安装失败解决方案:

     https://jingyan.baidu.com/article/fb48e8bee50ebf6e632e1464.html

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232603811.png" alt="image-20231121232603811" style="zoom:50%;" />

* **linux安装**

```linux
yum install -y git
```

### 1.2 git结构——本地库、暂存区、工作区

![image-20231121232638934](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232638934.png)

### 1.3 远程库介绍（代码托管）

**代码托管中心的任务：** **维护远程库**

* 局域网环境下

​		**GitLab** **服务器**

* 外网环境下

​		**GitHub**

​		**码云**

* **团队内部协作**

  <img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232849149.png" alt="image-20231121232849149" style="zoom:50%;" />

* **跨团队协作**

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231121232907993.png" alt="image-20231121232907993" style="zoom:50%;" />





## 第二章、git命令行操作

### 2.1 git init命令——本地库初始化

**切换到目录>右键Git Bash Here>用liunx命令到对应目录下>初始化**

```linux
git init
```

效果: 会在当前目录生成 **.git目录** (隐藏的)

### 2.2 设置签名——本地库初始化后,要执行的

**形式**

​	用户名：tom

​	Email 地址：goodMorning@atguigu.com

​	作用：区分不同开发人员的身份

​	辨析：这里设置的签名和登录远程库（代码托管中心）的账号、密码没有任何关系

**命令**

**项目级别** / **仓库级别**：(不带参数-)仅在当前本地库范围内有效

```linux
git config user.name tom_pro						#设置用户名

git config user.email goodMorning_pro@taku.com		#设置邮箱地址
```

* 信息保存位置：**./.git/config** **文件**

**系统用户级别：**登录当前操作系统的用户范围

```linux
git config --global user.name tom_pro						#设置用户名

git config --global user.email goodMorning_pro@taku.com		#设置邮箱地址
```

* 信息保存位置：**~/.gitconfig** **文件**

**级别优先级**

1. 就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别的签名

2. 如果只有系统用户级别的签名，就以系统用户级别的签名为准
3. 二者都没有不允许

## 第三章、基本操作

### 3.1 git status命令——查看工作区、暂存区状态

```linux
git status 				#第1代表是那个分区的,第2是否提交3有没有可提交的文件和提示
```

### 3.2 git add [file name]——工作区提交到暂存区

 /*提交到暂存区,并且转换换行符

```linux
git add [file name]				#将工作区的“新建/修改”添加到暂存区
```

### 3.3 git commit——提交到本地库

将暂存区的内容提交到本地库 

```linux
git commit [file name] [备注信息]

git commit -m "备注信息" [file name]
```



### 3.4 git rm [--cached -f]——暂存区撤回

* rm       仅删除工作区文件，并没有删除版本库的文件，想要删除版本库文件还要add和commit
* git rm     删除工作区**未修改**文件，并且将这次删除放入暂存区，想要删除版本库文件只要commit
* git rm  -f     删除工作区**已修改**文件，并且将这次删除放入暂存区，想要删除版本库文件只要commit
* git rm --cached     删除了暂存区和版本库的文件，但保留了工作区的文件，并且将这次删除放入暂存区，想要删除版本库文件只要commit。

#### 3.4.1 rm——删除工作区文件

```linux
rm [file name]
```

rm 命令只是删除工作区的文件，并没有删除版本库的文件，想要删除版本库文件还要执行下面的命令：

```linux
git add [file name]
git commit -m "delete [file name]"
```

**结果：** 删除了工作区和版本库的文件。

#### 3.4.2 git rm——删除工作区文件，并且将这次删除放入暂存区。

**注意：** 要删除的文件是没有修改过的，就是说和**当前版本库文件的内容相同**。

```linux
git rm [file name]
```

查看状态（成功删除了工作区文件，并且将这次删除放入暂存区。）

然后提交：

```linux
git commit -m "delete [file name]"
```

**结果：** 删除了工作区和版本库的文件，因为暂存区不可能有该文件（如果有意味着该文件修改后 git add 到暂存区，那样 git rm 命令会报错，如下面的情况）。

#### 3.4.3 git rm -f——删除工作区和暂存区文件，并且将这次删除放入暂存区。

**注意：** 要删除的文件已经修改过，就是说和**当前版本库文件的内容不同**。

```linux
git rm -f [file name]
```

然后提交：

```linux
git commit -m "delete [file name]"
```

**结果：** 删除了工作区、暂存区和版本库的文件。

#### 3.4.4 git rm --cached——删除暂存区文件，但保留工作区的文件，并且将这次删除放入暂存区。

删除暂存区文件，但保留工作区的文件，并且将这次删除放入暂存区

```linux
git rm --cached [file name]
```

然后提交：

```
git commit -m "delete [file name]"
```

**结果：** 删除了暂存区和版本库的文件，但保留了工作区的文件。如果文件有修改并 git add 到暂存区，再执行 git rm --cached 和 git commit，那么保留的工作区文件是修改后的文件，同时暂存区的修改文件和版本库的文件也被删了。

### 3.5 git log——查看本地库版本记录

```linux
git log							#查看本地库版本记录,空格向下翻页 ,b 向上翻页 ,q 退出(超过了自动多屏)
git log --pretty=oneline		#每个历史只显示一行(hash值和日志),更人性化
git log oneline					#每个历史只显示一行(hash值和日志)，且hash值只显示部分,更人性化
git reflog						#显示历史只显示一行,并且显示指针(要移动到版本多少步)，很强大
```

### 3.6 git reset——前进后退

在git reflog的基础上

```linux
git reset --hard [局部索引值]			#基于索引值操作
git reset --hard HEAD^^					#使用^符号，只能后退到先前版本，一个^表示后退一步
git reset --hard HEAD~n					#使用~符号，只能后退，n表示后退 n 步
```

**git reset三个参数对比：**

* --soft

​			**仅仅在本地库移动** HEAD 指针 (查看状态时,绿色提示,本地库和暂存区不同步)

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231122235837688.png" alt="image-20231122235837688" style="zoom:50%;" />

* --mixed

​			在本地库移动 HEAD 指针

​			重置**暂存区**

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231122235928162.png" alt="image-20231122235928162" style="zoom:50%;" />

* --hard

​			在本地库移动 HEAD 指针

​			**重置暂存区**

​			**重置工作区**

### 3.7 git diff——比较文件的差异

```linux
git diff [文件名]						#比较工作区的文件和暂存区的文件差异
git diff [本地库版本索引值] [文件名]		#通过版本索引比较本地库和工作区文件差异
git diff [HEAD^] [文件名]				#通过HEAD指针比较本地库和工作区文件差异
```

**不带文件名会比较多个文件**

### 3.8 分支操作

同时并行推进多个功能开发，提高开发效率

各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

* 创建分支

```linux
git branch [分支名]
```

* 查看分支

```linux
git branch -v
```

* 切换分支

```linux
git checkout [分支名]
```

* 合并分支

```linux
git merge [有新内容分支名]	
```

​		1. 第一步:切换到接受修改的分支(被合并,增加新内容)上

​		2. 第二步：执行 merge 命令 (合并分支指令)

* 解决冲突

冲突原因: 2个分支,修改同一文件,同一位置,修改内容不一样时.

![image-20231123171840115](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123171840115.png)

**冲突的解决:**

1. 第一步：编辑文件，删除特殊符号

2. 第二步：把文件修改到满意的程度，保存退出

3. 第三步：git add [文件名]

4. 第四步：git commit -m "日志信息"

**注意：此时** **commit** **一定不能带具体文件名**





## 第四章、远程库操作——github操作

### 4.1 创建远程库

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172125876.png" alt="image-20231123172125876" style="zoom:50%;" />

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172133865.png" alt="image-20231123172133865"  />

### 4.2 创建远程库地址别名

* 远程库地址

![image-20231123172216232](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172216232.png)

* 查看各远程地址别名

```linux
git remote -v 							#查看当前所有远程地址别名 
```

* 创建别名

```linux
git remote add [别名] [远程地址]
```

### 4.3 本地库推送到远程库

```linux
git push [别名] [分支名]
git push [远程地址] [分支名]
```

**可能需要等待一会会,弹出对话框  >  输入用户和密码)**

### 4.4 克隆——远程库下载到本地

![image-20231123172724723](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172724723.png)

```linux
git clone [远程地址]
```

**克隆效果:**

​	**完整的把远程库下载到本地**

​	**创建** **origin** **远程地址别名** (git remote -v查看远程库别名)

​	**初始化本地库**(就是:git init)

### 4.5 团队成员邀请

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172915874.png" alt="image-20231123172915874" style="zoom:50%;" />

![image-20231123172927557](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172927557.png)

![image-20231123172943872](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123172943872.png)

“岳不群”其他方式**把邀请链接发送给“令狐冲”，“****令狐冲”****登录自己的** **GitHub** **账号，访问邀请链接。**

点击接受 >然后在执行推送

![image-20231123173202873](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123173202873.png)

* 推送了第一次后再次推送不要输入用户名

* git 本身不具备记录功能,Windows中**凭据管理器**记录用户名和密码

**控制面板** -> **所有控制面板项** -> **凭据管理器** (如果想切换用户:删除记录)

![image-20231123173342702](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123173342702.png)

### 4.6 pull——拉取

pull=fetch+merge

```linux
git pull [远程库地址别名] [远程分支名]   
```

等同于下面步骤

```
git fetch [远程库地址别名origin] [远程分支名master]   #抓取下来
git checkout origin/master						#切换到链接地址(别名)的master(可查看抓取下来内容
git checkout master								#切换回
git merge [远程库地址别名origin/master远程分支名]   #合并
```

### 4.7 远程库解决冲突

* 如果不是基于 GitHub 远程库的最新版所做的修改，不能推送，必须先拉取。

* 拉取下来后如果进入冲突状态，则按照**分支冲突解决**操作解决即可。

### 4.8 跨团队协作

dfbb表示开发人员，ybq表示审核人员

* (先复制当前库地址,发式给dfbb,然后有dfbb登录访问这个地址)>然后Fork

![image-20231123174119353](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174119353.png)

fork 过来的仓库说明 回多下面一行(forked from at...)说明fork来源

![image-20231123174148580](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174148580.png)

* dfbb(”东方不败”)本地修改，然后推送到远程 git push origin master

* dfbb在远程库中选择Pull Request

![image-20231123174223177](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174223177.png)

​			1. 然后点击里面的New pull requset![image-20231123174242711](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174242711.png)

​			2. 然后点击 Create pull request![image-20231123174259344](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174259344.png)

​			3. 然后发送消息给,fork的库(ybq(岳不群))

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174330012.png" alt="image-20231123174330012" style="zoom:50%;" />

* ybq操作（审核）

<img src="C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174427374.png" alt="image-20231123174427374"  />

![image-20231123174437013](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174437013.png)

* 可对话

![image-20231123174513127](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174513127.png)

* 审核代码

![image-20231123174532892](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174532892.png)

* 合并代码

合并代码 (回到对话Conversation>>合并操作如图)

![image-20231123174605959](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174605959.png)

![image-20231123174633071](C:\Users\xieshidu\AppData\Roaming\Typora\typora-user-images\image-20231123174633071.png)