## Git第一天
### Git诞生的历史
> 很多人都知道，Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。
> Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？
> 事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！
> 你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。
> 不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。
> 安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。
> Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：
> Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。
> Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。
> 历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。

### Git的安装
> 1. Git官网地址: http://gitforwindows.org/
>    安装过程示例：
> 2. 查看当前电脑是32位还是64位的,找到对应的版本来安装
> 3. 开始安装Git
>    ![2345截图20180109154409.png](http://upload-images.jianshu.io/upload_images/122816-1e05e390e52e8fa5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154558.png](http://upload-images.jianshu.io/upload_images/122816-5c3ec27679f02671.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154638.png](http://upload-images.jianshu.io/upload_images/122816-7f185fd620805e55.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154659.png](http://upload-images.jianshu.io/upload_images/122816-bcab55872ffe7037.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154713.png](http://upload-images.jianshu.io/upload_images/122816-0bb86156be940e86.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154727.png](http://upload-images.jianshu.io/upload_images/122816-5c8dd8556a26bae3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154742.png](http://upload-images.jianshu.io/upload_images/122816-998093322457b208.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154756.png](http://upload-images.jianshu.io/upload_images/122816-0275259fa6972344.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154812.png](http://upload-images.jianshu.io/upload_images/122816-a8a9310d7dcca45b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180109154946.png](http://upload-images.jianshu.io/upload_images/122816-7bd698d0b37655a2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Git的简单配置
> 打开Git的命令窗口
> 在要使用的文件夹通过鼠标右键，选择Git Bash Here来打开命令窗口
> 配置命令窗口的显示文字大小

### 认识Shell
> Shell是用户和Linux操作系统之间的接口.Linux中有多种shell,其中缺省使用的是Bash.Shell俗称壳,用来区别于Kernel(核), 是指'提供使用者使用界面'的软件(命令解析器).它类似于DOS下的command和后来的cmd.exe.它接收用户命令,然后调用相应应用程序.
> - 图形界面Shell:通过提供友好的可视化界面,调用相应应用程序,如windows系列操作系统,Linux系统上的图形化应用程序GNOME,KDE等.
> - 命令行Shell: 通过键盘输入特定命令的方式,调用相应的应用程序,如windows系统的cmd.exe, Windows PowerShell, Linux系统的Bourne shell(sh), Bourne Again shell(Bash)等.Linux默认使用Bash,所以我们要学习的就是以Bash为基础的.Git软件内置了Bash.我们可以直接在里面进行命令操作.
>
> ![image](http://upload-images.jianshu.io/upload_images/122816-06fffbeb21866cfc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Bash命令
> 常见命令格式: 命令[-options][参数]
> * ```cd (Change Directory)``` 切换目录，如 cd /etc
> * ```ls (List)``` 查看当前目录下内容，如 ls -al, ls -l
> * ```pwd(Print Working Directory)``` 查看当前目录
> * ```mkdir (Make Directory) ``` 创建目录，如 mkdir blog
> * ```touch``` 创建文件，如 touch index.html
> * ```wc (Word Count) ``` 字数信息统计，如 wc index.html
> * ```wc -l filename ``` 报告行数
> * ```wc -c filename ``` 报告字节数
> * ```wc -m filename ``` 报告字符数
> * ```wc -w filename ``` 报告单词数
> * ```cat ``` 查看文件全部内容，如 cat index.html
> * ```more less ``` 查看文件，如more /etc/passwd、less /etc/passwd
> * ```rm (remove) ``` 删除文件，如 rm index.html、rm -rf  blog
> * ```rmdir (Remove Directory) ``` 删除文件夹，只能删除空文件夹，不常用
> * ```mv (move)  ``` 移动文件或重命名，如 mv index.html ./demo/index.html
> * ```cp (copy)  ``` 复制文件，cp index.html ./demo/index.html
> * ```head ``` 查看文件前几行，如 head -5 index.html
> * ```tail  ``` 查看文件后几行 –n –f，如 tail index.html、tail -5 index.html 
> * ```tab  ``` 自动补全，连按两次会将所有匹配内容显示出来
> * ```history  ``` 查看操作历史
> * ```ssh  ``` 远程登录，如ssh root@gitlab.study.com
> * ```> 和 >> ``` 重定向，如echo hello world! > README.md，>覆盖 >>追加,把原来输入的内容，自己指定到别的地方。把原本输出到屏幕上的内容，写入到指定的文件当中。如果文件不存在，会自动帮你创建文件。
> * ```wget  ``` 下载，如wget https://nodejs.org/dist/v4.4.0/node-v4.4.0.tar.gz
> * ```tar   ``` 解压缩，如tar zxvf node-v4.4.0
> * ```curl   ``` 网络请求，如curl http://www.baidu.com
> * ```who am i  ``` 查看当前用户
> * ```|   ``` 管道符,把上一次的结果(输出)当做下一次的参数(输入)。
> * ```grep ``` 匹配内容，一般结合管道符使用

### Vi编辑器
> Vi编辑器是Linux和Unix上最基本的文本编辑器，工作在字符模式下。由于不需要图形界面，Vi是效率很高的文本编辑器。尽管在Linux上也有很多图形界面的编辑器可用，但vi在系统和服务器管理中的功能是那些图形编辑器所无法比拟的。类似于Window下的记事本.
> Vi编辑器有三种模式.只要记住三种编辑模式.操作Vi编辑器是非常方便的.三种模式分别为:
> 1). 命令行模式
> 2). 输入模式
> 3). 末行模式
> 三种模式的切换如图所示:
> ![image](http://upload-images.jianshu.io/upload_images/122816-8589a61d0a8d4bce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 在输入模式下是不能够直接切换到末行模式,必须得先回到命令模式.
> 	* 我们可以通过Esc键回到命令模式.
> 	* 每一种编辑下面有对应的命令.
> * 输入模式命令
	* 直接输入i或者a进入输入模式,可以进行内容的编辑
	* 想要退出输入模式,则按下键盘的Esc键
> * 末行模式命令
	* 进行末位模式: `shift + :`
	* ` w`: 保存当前文件
	* ` w` filePath/fileName: 另存为
	* ` wq`: 保存并退出
	* ` e!`: 撤销更改,返回上一次保存状态
	* ` q!`: 不保存,强制退出.
	* `set nu`: 设置行号
> * 命令模式
	* `ZZ`: (大写)保存并直接退出
	* `yy`: 复制当前行
	* `u`: 撤销操作,可以撤销多次
	* `dd`: 删除当前行
	* `p`: 粘贴内容
	* `ctrl + f`: 向前翻页.
	* `ctrl + b`: 向后翻页
	 
### 版本控制
> 版本控制（Version Control Systems）是一种软体工程技巧，在开发的过程中，确保由不同人所编辑的同一档案都得到更新。版本控制通过文档控制(documentation control)记录程序各个模块的改动,并为每次改动编上序号.这种方法时工程图(engineering drawings) 维护 (maintenance)的标准做法.
> 版本控制分为两种:
> 1. 集中式管理
>    > 实际开发环境,一个项目通常是由多人写作共同完成的,如何让在不同系统上的开发者协同工作成为了必须解决的问题,集中式版本控制系统便应运而生了,它通过单一的集中管理的服务器,保存所有文件的修订版本,协同工作的开发者都通过客户端连到这台服务器,取出最新的文件或提交更新,其代表就是SVN.
>    > 工作流程如图所示:
>    > ![image](http://upload-images.jianshu.io/upload_images/122816-91005d3e4f2af8f6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    > 这种方式很好的解决了多人协同开发的问题,但是有一个弊端.如果集中管理的服务器出现故障,将会导致数据(版本)丢失的风险.如果协同开发者从集中服务器中更新数据时,严重依赖网络,如果网络不佳,将会给开发带来很多不便.
> 2. 分布式管理
>    > 分布式版本控制系统,则不需要中央服务器,每个开发者都拥有一个完整的版本库,这么一来,任何协同开发者使用的服务器发生故障,事后都可以用其他协同开发者本地仓库回复.由于版本库在本地计算机,便不再受网络影响了,如果要将本地的修改,推送给其他协同开发者,还需要一台共享服务器,所有开发者通过这台共享服务器提交和更新数据.
>    > 工作流程如图所示:
>    > ![image](http://upload-images.jianshu.io/upload_images/122816-0a02ca8e9a7bb491.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    > 分布式版本控制系统弥补了前面两种版本控制系统的缺陷,成为了版本控制的首选方案,其代表就是Git.

### Git的工作原理
> 为了更好的学习Git,我们必须了解Git管理我们文件的3中状态. 分别是:
> 1. 已提交(committed) 没有任何提示
> 2. 已修改(modified) (没有纳入到版本控制) 红色
> 3. 已暂存(staged) 绿色
> 4. 由此引入Git项目的三个工作区域概念
>    > Git仓库:
>    > 是Git用来保存项目的元数据和对象数据库的地方.这是Git中最重要的部分,从其他计算机克隆仓库时,拷贝的就是这里的数据.
>    > 工作目录:
>    > 是对项目的某个版本独立提取出来的内容.这些从Git仓库的压缩数据库中提取出来的文件,放在磁盘上供你使用或修改.
>    > 暂存区域:
>    > 是一个文件,保存了下次将提交的文件列表信息,一般在Git仓库目录中.有时候也被称作'索引'(Index),不过一般说法还是叫暂存区域
>    > 基本的Git工作流程如下:
>    > 1. 在工作目录中修改文件;
>    > 2. 暂存文件,将文件的快照放入暂存区域;
>    > 3. 提交更新,找到暂存区域的文件,将快照永久性存储到Git仓库目录. 
>    >    如下图所示:
>    >    ![image](http://upload-images.jianshu.io/upload_images/122816-29bec17e6b215916.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Git的命令
#### 常用命令:
> 配置用户:
>  ```
>   git config --global user.name "自已的名字"
>   git config --global user.email "自已的邮箱地址"
>  ```
>  * 初始化仓库: git init 
>  * 查看当前状态: git status
>  * 提交本地文件到缓存区: git add -A(提交所有的)
>  * 将缓存区的东西提交到本地仓库: git commit -m"提交信息"
>  * 查看所有的提交日志: git log
>  * 回退到某一个版本: git reset --hard sha值
>  * 回退到修改状态: git reset --mixed(默认可以不写) sha值
>  * 回退到暂存区状态: git reset --soft sha值
>  * 将本地仓库的内容提交到远程服务器: git push
>  * 从远程服务器更新: git pull
>  * 查看所有的sha值: git reflog

### Git的基本使用示例
> * 第一步: 使用命令行在桌面上创建一个文件夹code、
> ![2345截图20180109162707.png](http://upload-images.jianshu.io/upload_images/122816-e42d2d462b44f6e4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109162728.png](http://upload-images.jianshu.io/upload_images/122816-4aea8badeb6fe43c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第二步： 切换到code文件夹下，创建index.txt文件,并初始化Git仓库
> ![2345截图20180109163039.png](http://upload-images.jianshu.io/upload_images/122816-190481c8d670f498.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109163229.png](http://upload-images.jianshu.io/upload_images/122816-78839d2434a90aa6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> win7下开启显示隐藏的文件夹
> ![2345截图20180109163511.png](http://upload-images.jianshu.io/upload_images/122816-4b9d08f76c1266bf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109163551.png](http://upload-images.jianshu.io/upload_images/122816-c7947598c044ce2e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第三步: 查看文件状态
> ![2345截图20180109164112.png](http://upload-images.jianshu.io/upload_images/122816-18a8df3288a23b89.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第四步: 添加文件到暂存区
> ![2345截图20180109164354.png](http://upload-images.jianshu.io/upload_images/122816-17239ba30b5d38cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第五步: 提交文件到本地仓库
> ![2345截图20180109164750.png](http://upload-images.jianshu.io/upload_images/122816-2465e181969c1647.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第六步: 配置用户名和邮箱
> ![2345截图20180109165138.png](http://upload-images.jianshu.io/upload_images/122816-afea0eb7597b4ac9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109165246.png](http://upload-images.jianshu.io/upload_images/122816-74227796fb803c3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109165417.png](http://upload-images.jianshu.io/upload_images/122816-62ef452b86eff327.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109165639.png](http://upload-images.jianshu.io/upload_images/122816-4cb0bea4a311e0b0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109165708.png](http://upload-images.jianshu.io/upload_images/122816-409ff32bf504bf82.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第七步: 查看提交的历史
> ![2345截图20180109170208.png](http://upload-images.jianshu.io/upload_images/122816-8665856ff011eff0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第八步: 对文件进行修改,再次查看文件状态,发现为modified状态,此时需要再次把它提交到暂存区并提交本地仓库
> ![2345截图20180109171039.png](http://upload-images.jianshu.io/upload_images/122816-351c6cdcee1f51ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第九步： 回退到第一个版本
> ![2345截图20180109171525.png](http://upload-images.jianshu.io/upload_images/122816-8ab39d02ae380de8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 有关分支操作的命令:
> * 开启分支: git branch fixBranch(分支名称)
> * 查看当前分支 有*的代表当前正在工作的分支: git branch
> * 切换到fixBranch的分支上: git checkout fixBranch
> * 分支合并,将fixBranch上的内容合并到master上: git merge fixBranch
> * 删除分支: git branch -d fixBranch

### 分支使用示例
> * 查看历史版本
> ![2345截图20180109172136.png](http://upload-images.jianshu.io/upload_images/122816-0891040e719f58f9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第一步：创建分支，查看分支
> ![2345截图20180109172631.png](http://upload-images.jianshu.io/upload_images/122816-f41e7d63fa1901a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第二步： 切换分支
> ![2345截图20180109172845.png](http://upload-images.jianshu.io/upload_images/122816-088ed5a6385ab708.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第三步：在新分支下，添加一些代码
> ![2345截图20180109173338.png](http://upload-images.jianshu.io/upload_images/122816-a4524cd44254aa60.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109173433.png](http://upload-images.jianshu.io/upload_images/122816-b92b9778cc4cee86.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第四步： 再次切换到主分支，查看日志，发现并没有在developer分支中添加的日志，查看文件也没有在developer分支添加的内容
> ![2345截图20180109173855.png](http://upload-images.jianshu.io/upload_images/122816-ae16990e462501a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109173935.png](http://upload-images.jianshu.io/upload_images/122816-af6afba986d9b16e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第五步： 合并分支，合并分支后，在master分支上，可以看到所有提交的历史日志和在developer分支所添加的文件
> ![2345截图20180109174532.png](http://upload-images.jianshu.io/upload_images/122816-6bcfa474f7c8fd47.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109174634.png](http://upload-images.jianshu.io/upload_images/122816-7b5497fd7a7a9e44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第六步： 删除分支
> ![2345截图20180109174831.png](http://upload-images.jianshu.io/upload_images/122816-fc67dc98566af07c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Git多人共享代码示例
> * 在实际开发中，多个开发者之间经常需要互相拷贝代码，以下是相关示例
> * 第一步： 在code文件夹中创建两个文件夹，分别为user1和user2，代表两个用户
> ![2345截图20180109184702.png](http://upload-images.jianshu.io/upload_images/122816-1d072f06721c25a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第二步： user1用户创建一个项目，并且纳入到Git的版本控制
> ![2345截图20180109185150.png](http://upload-images.jianshu.io/upload_images/122816-414ec9f8928cfeb6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109185211.png](http://upload-images.jianshu.io/upload_images/122816-928a4a12ad70f635.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第三步： user2用户想要拷贝user1的代码，做如下操作
> ![2345截图20180109185556.png](http://upload-images.jianshu.io/upload_images/122816-e26dbcf919f1e3e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109185920.png](http://upload-images.jianshu.io/upload_images/122816-91a2faeb86d8fffe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第四步： user2用户修改代码，并且提交到本地仓库
> ![2345截图20180109190204.png](http://upload-images.jianshu.io/upload_images/122816-70b2c738e05375b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109190420.png](http://upload-images.jianshu.io/upload_images/122816-95b4e4eef35e340c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第五步:  user1用户想要拷贝user2用户的代码的话，此时需要执行更新命令
> ![2345截图20180109190828.png](http://upload-images.jianshu.io/upload_images/122816-9a51296feaab8b2b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109190940.png](http://upload-images.jianshu.io/upload_images/122816-bf15aed93d48e1a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Git共享仓库相关命令
> 从仓库克隆代码: git clone 仓库地址
> 创建一个本地共享仓库: git clone --bare 仓库地址或者名称

### Git共享仓库示例
> * 共享仓库,虽然是一个裸仓库,但是它克隆下来的内容,是一个完整的仓库,里面是有工作区域的,但是看不到,它把工作区隐藏了,不让你去修改里面的内容,它是用来共享的,不能修改任何源代码;
> * 第一步： 在桌面创建一个Progect文件夹，文件夹中存放三个文件夹为shareProgect，user1和user2，分别代表本地共享库，用户1和用户2
> ![2345截图20180109191617.png](http://upload-images.jianshu.io/upload_images/122816-31977c1d420f971a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第二步： 在user1用户中创建一个project文件夹，代表一个项目并初始化index.txt文件纳入到git版本控制
> ![2345截图20180109191916.png](http://upload-images.jianshu.io/upload_images/122816-36b0b9fb0d55cfa6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109192010.png](http://upload-images.jianshu.io/upload_images/122816-1bfaddfe3504fea7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第三步： 在shareProgect文件夹创建共享仓库
> ![2345截图20180109192341.png](http://upload-images.jianshu.io/upload_images/122816-fd7d1c2e77a32a64.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109192528.png](http://upload-images.jianshu.io/upload_images/122816-1fc61ff5753a56e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109192639.png](http://upload-images.jianshu.io/upload_images/122816-661dd2780d2464cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第四步： user2拉取共享仓库的代码，并作出修改，提交到共享仓库
> ![2345截图20180109193550.png](http://upload-images.jianshu.io/upload_images/122816-3cf915267b879b96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109193657.png](http://upload-images.jianshu.io/upload_images/122816-c118d31632110137.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109193906.png](http://upload-images.jianshu.io/upload_images/122816-0ed9c6253304a674.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109194158.png](http://upload-images.jianshu.io/upload_images/122816-b0d2b83c6b51fe6d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109194350.png](http://upload-images.jianshu.io/upload_images/122816-ec5a0fff50154c21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第五步： user1更新共享仓库中的最新代码
> ![2345截图20180109194613.png](http://upload-images.jianshu.io/upload_images/122816-af736dad4a0fea5f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109194649.png](http://upload-images.jianshu.io/upload_images/122816-9c5c99d86be48602.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Git共享仓库代码冲突示例
> * 代码冲突: 多个人同时修改了相同的代码,并且都提交到了本地,先提交到远程仓库的人不会有任何问题!后提交的人,需要先pull下来,在pull的时候,会产生冲突;
> 	* 这个时候就需要先去解决冲突,解决完毕后,提交到本地,再提交到远程仓库;
> * 第一步：user2修改了login.txt，并将它提交到了远程仓库
> ![2345截图20180109200525.png](http://upload-images.jianshu.io/upload_images/122816-9e05f33634a36e0e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109200407.png](http://upload-images.jianshu.io/upload_images/122816-0328419b2a53b489.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第二步：user1同样修改login.txt,将它提交到本地仓库
> ![2345截图20180109200835.png](http://upload-images.jianshu.io/upload_images/122816-e82942ea26dd9da5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109202121.png](http://upload-images.jianshu.io/upload_images/122816-75c38e1409fa7c0a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第三步： user1将代码提交到远程仓库，会发生冲突，,因为user1跟user2修改了同一个文件的同段代码,而且user1已经提交到远程仓库,远程仓库的版本比user1的版本要新，此时提示user1在push之前先执行git pull
> ![2345截图20180109202711.png](http://upload-images.jianshu.io/upload_images/122816-415e054259013ae5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第四步： user1执行git pull，在执行git pull时，提示login.txt文件产生冲突，要去解决冲突
> ![2345截图20180109203536.png](http://upload-images.jianshu.io/upload_images/122816-32ab893f3c263be1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 	* 打开user1文件夹里面的login.txt文件
> ![2345截图20180109203853.png](http://upload-images.jianshu.io/upload_images/122816-e546d028d22f98b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 	* 解决冲突，根据实际开发的需要删除对应的<<<===，保留最终的代码就可以
> ![2345截图20180109204116.png](http://upload-images.jianshu.io/upload_images/122816-c0ed3e717a48dc8a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第五步： user1再次提交代码到本地，提交到共享仓库
> ![2345截图20180109204435.png](http://upload-images.jianshu.io/upload_images/122816-fccceec5affc9d13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * 第六步： user2从共享仓库拉取代码，此时代码和user1一样
> ![2345截图20180109204743.png](http://upload-images.jianshu.io/upload_images/122816-34f31a4ceb28ebe7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180109204840.png](http://upload-images.jianshu.io/upload_images/122816-5103adf299fa6805.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
