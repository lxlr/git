## Git第二天
### 对称加密
> 在密码学中，加密是将明文信息隐匿起来，使之在缺少特殊信息时不可读。
> 加密，是以某种特殊的算法改变原有的信息数据，使得未授权的用户即使获得了已加密的信息，但因不知解密的方法，仍然无法了解信息的内容。
> 下面是对称加密的示例图:
> ![对称加密.jpg](http://upload-images.jianshu.io/upload_images/122816-78684231a4538672.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 采用单钥密码系统的加密方法，同一个密钥可以同时用作信息的加密和解密，这种加密方法称为对称加密，也称为单密钥加密。
> 所谓对称，就是采用这种加密方法的双方使用方式用同样的密钥进行加密和解密。密钥是控制加密及解密过程的指令。算法是一组规则，规定如何进行加密和解密。
> 在对称加密算法中常用的算法有：DES、3DES、TDEA、Blowfish、RC2、RC4、RC5、IDEA、SKIPJACK、AES等。
> 对称加密算法的优点是算法公开、计算量小、加密速度快、加密效率高。
> 对称加密算法的缺点是在数据传送前，发送方和接收方必须商定好秘钥，然后使双方都能保存好秘钥。其次如果一方的秘钥被泄露，那么加密信息也就不安全了。另外，每对用户每次使用对称加密算法时，都需要使用其他人不知道的唯一秘钥，这会使得收、发双方所拥有的钥匙数量巨大，密钥管理成为双方的负担.
> 对称加密举个例子:
> 比如现实生活中,甲公司从乙公司定的货物,通常采用货柜车来送,为了保证货物的安全,货柜车的钥匙由甲公司老板和乙公司老板保管,当货柜车到达以后就可以用这个钥匙打开,当送货物的时候就可以将货柜车锁上.

### MD5加密
> MD5算法具有以下特点：
> 1. 压缩性：任意长度的数据，算出的MD5值长度都是固定的。
> 2. 容易计算：从原数据计算出MD5值很容易。
> 3. 抗修改性：对原数据进行任何改动，哪怕只修改1个字节，所得到的MD5值都有很大区别。
> 4. 强抗碰撞：已知原数据和其MD5值，想找到一个具有相同MD5值的数据（即伪造数据）是非常困难的。

### 非对称加密
> 非对称加密算法需要两个密钥来进行加密和解密，这两个秘钥是公开密钥（public key，简称公钥）和私有密钥（private key，简称私钥）。
> 非对称加密算法需要两个密钥：公开密钥（publickey）和私有密钥（privatekey）。公开密钥与私有密钥是一对，如果用公开密钥对数据进行加密，只有用对应的私有密钥才能解密；如果用私有密钥对数据进行加密，那么只有用对应的公开密钥才能解密。因为加密和解密使用的是两个不同的密钥，所以这种算法叫作非对称加密算法。
> 下面是非对称加密的示例图:
> ![非对称加密.jpg](http://upload-images.jianshu.io/upload_images/122816-07dec5202d5d9f3b.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 如图所示加密过程:
> 1. 乙方生成一对密钥（公钥和私钥）并将公钥向其它方公开。
> 2. 得到该公钥的甲方使用该密钥对机密信息进行加密后再发送给乙方。
> 3. 乙方再用自己保存的另一把专用密钥（私钥）对加密后的信息进行解密。乙方只能用其专用密钥（私钥）解密由对应的公钥加密后的信息。
>    在传输过程中，即使攻击者截获了传输的密文，并得到了乙的公钥，也无法破解密文，因为只有乙的私钥才能解密密文。
>    同样，如果乙要回复加密信息给甲，那么需要甲先公布甲的公钥给乙用于加密，甲自己保存甲的私钥用于解密。
>    在非对称加密中使用的主要算法有：RSA、Elgamal、背包算法、Rabin、D-H、ECC（椭圆曲线加密算法）等。
>    非对称加密与对称加密相比，其安全性更好：对称加密的通信双方使用相同的秘钥，如果一方的秘钥遭泄露，那么整个通信就会被破解。而非对称加密使用一对秘钥，一个用来加密，一个用来解密，而且公钥是公开的，秘钥是自己保存的，不需要像对称加密那样在通信之前要先同步秘钥。
>    非对称加密的缺点是加密和解密花费时间长、速度慢，只适合对少量数据进行加密。

### SSH免密码登录原理
> 1. 客户端生成公钥和私钥,并和服务端建立连接,将公钥发送给服务端;
> 2. 客户端请求连接,服务端生成一段随机的字符串,将该字符串用客户端的公钥加密后和服务端自己的公钥发送给客户端;
> 3. 客户端用自己的私钥解密该字符串,并使用服务端的公钥加密后,发送给服务端;
> 4. 服务端使用自己的私钥解密该字符串,和生成的随机字符串对比,如果相同则连接建立.
>    示例图如下:
>    ![Snip20180102_65.png](http://upload-images.jianshu.io/upload_images/122816-1a8f57bf0396e869.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 本地生成公钥私钥命令
> 生成 公钥/私钥: ssh-keygen -t rsa

### github创建仓库步骤
> 1. 生成公钥和私钥
>    ![2345截图20180102105605.png](http://upload-images.jianshu.io/upload_images/122816-4dd1ea79d341d2ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 2. 登录github帐号添加本地公钥
>    ![2345截图20180102110505.png](http://upload-images.jianshu.io/upload_images/122816-0b92c4db2cb0cdf5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180102111457.png](http://upload-images.jianshu.io/upload_images/122816-94db327ccd5c4037.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102111631.png](http://upload-images.jianshu.io/upload_images/122816-15860f75b51e9732.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102111809.png](http://upload-images.jianshu.io/upload_images/122816-9f67efb3d8938a32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102111929.png](http://upload-images.jianshu.io/upload_images/122816-b28dbc594ee31dc4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    1. 创建仓库
>       ![2345截图20180102112706.png](http://upload-images.jianshu.io/upload_images/122816-2019041cc119d662.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102113057.png](http://upload-images.jianshu.io/upload_images/122816-a0aff6f3dcbd8ff1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    1. 克隆地址
>       ![2345截图20180102114155.png](http://upload-images.jianshu.io/upload_images/122816-3d7ebbbc00a065a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102114428.png](http://upload-images.jianshu.io/upload_images/122816-10bb11d14b8c8dd1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102114747.png](http://upload-images.jianshu.io/upload_images/122816-8903cccb63d55c9c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>
>    ![2345截图20180102114859.png](http://upload-images.jianshu.io/upload_images/122816-71ef9e1c9e94f43c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 代码托管平台
> GitHub
> 	> GitHub的地址: https://github.com/
> GitLab
> 	> Gitlab支持无限的公有项目和私有项目。Gitlab地址：https://about.gitlab.com/
> Bitbucket
> 	> bitbucket 免费支持5个开发成员的团队创建无限私有代码托管库 。bitbucket地址：https://bitbucket.org/
> (推荐)开源中国代码托管 码云
> 	> 开源中国一个账号最多可以创建1000个项目，包含公有和私有，开源中国代码托管地址：http://git.oschina.net/
> 	> 开源中国在几个月前又发布了团队协作开发平台，和代码托管平台一起，打造了一个十分好的团队开发平台，开源中国团队协作平台地址：http://team.oschina.net/，团队协作平台支持任务的创建、讨论、便签等.
> (推荐)coding.net 码市
> 	> 谈到coding.net,首先必须提的是速度快，功能与开源中国相似，同样一个账号最多可以创建1000个项目，也支持任务的创建等。coding.net地址：https://coding.net/home.html.
> CSDN代码托管
> 	> CSDN代码托管地址：https://code.csdn.net/

### Git忽略文件
> 在开发中,有些时候,我们必须把某些文件存放在Git的工作目录中,但是又不能提交它们,比如说保存了数据库密码的配置文件啦,等等,每次git status都会显示Untracked files ...;
> Git提供了针对这种情况的解决方案就是在Git工作区的根目录下创建一个特殊的.gitignore文件,然后把需要忽略的文件名填进去,Git就会自动忽略这些文件.
> 不需要从头写.gitignore文件,GitHub已经我们准备了各种配置文件，只需要组合一下就可以使用了,所有的配置文件可以直接在线浏览：https://github.com/github/gitignore
> 下面是详细示例:
> 1.  首先在webStorm中打开testDemo这个项目,在index.html新增代码;
>      ![1.png](http://upload-images.jianshu.io/upload_images/122816-d1ea54d6ad0592bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 2.  在命令行查看当前项目的状态,发现多出来.idea文件夹下面一系列文件,先不理会它们,全部提交到GitHub;
>      ![2.png](http://upload-images.jianshu.io/upload_images/122816-ac8227bf6dd48f0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>      ![3.png](http://upload-images.jianshu.io/upload_images/122816-25c7f809dafaeca1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>      ![4.png](http://upload-images.jianshu.io/upload_images/122816-804c3b3e04ede04a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 3.  继续修改index.html文件,查看Git状态,发现.idea/workspace.xm龙文件发生变化,是因为在这个文件里面记录了webStrom相关的一些状态,每次修改项目,都会发生相应的改变,继续提交到远程的GitHub;
>     ![5.png](http://upload-images.jianshu.io/upload_images/122816-f30e9ea652444377.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![6.png](http://upload-images.jianshu.io/upload_images/122816-cf719ebc2a1a762d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![7.png](http://upload-images.jianshu.io/upload_images/122816-ede8c02d8a1a79a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 4.  .idea文件夹下面的文件都不需要提交,所以我们在提交的时候要忽略掉它,在项目的根目录创建.gitignore文件,注意:图形化界面不能创建该文件,
>     ![8.png](http://upload-images.jianshu.io/upload_images/122816-bb32bbb2b5c76dae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![9.png](http://upload-images.jianshu.io/upload_images/122816-913f9a96653633b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



> 1.  .gitignore文件的忽略规则: 
>     - node_modules/  代表node_modules下的所有文件都不提交
>     - node_modules/*.jpg  代表node_modules/123.jpg图片不提交但是node_modules/coderYDH/456.jpg可以提交
>     - .idea/*  代表 .idea 下的所有文件都不提交
>     - *.png  代表忽略所有的 .png 结尾的文件
>     - !xxoo.png  代表排除 xxoo.png
>       ![2345截图20180103112210.png](http://upload-images.jianshu.io/upload_images/122816-ce41a3ff30464748.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 2.  创建规则，提交.gitignore文件后,再次修改index.html文件,发现该忽略的还是没有忽略:
>     ![2345截图20180103114254.png](http://upload-images.jianshu.io/upload_images/122816-05b55340efc5113a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180103114412.png](http://upload-images.jianshu.io/upload_images/122816-9db613b1d5d729fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 3.  这里主要是因为.gitignore只能忽略那些原来没有被track的文件,如果某些文件已经被纳入到了版本管理中,修改.gitignore文件无效,解决方案就是先把本地缓存删除(改变成未track状态),然后再提交.
>     ![2345截图20180103115621.png](http://upload-images.jianshu.io/upload_images/122816-b4b95ccd715389ee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180103115705.png](http://upload-images.jianshu.io/upload_images/122816-874705a8e7321f44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180103115750.png](http://upload-images.jianshu.io/upload_images/122816-1447203e5d6e01b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180103115953.png](http://upload-images.jianshu.io/upload_images/122816-1d38bbd95b1bc54f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 有关远程操作分支的命令:
> 创建本地分支: git branch test
> 将本地分支推送到远程分支: git push origin test
> 删除本地分支: git branch -r -d origin/branch-name
> 删除远程分支: git push origin --delete test

### 有关远程操作仓库的命令
> 查看远程仓库地址,默认是origin: git remote -v 
> 添加一个远程仓库: git remote add 仓库名称/仓库地址 
> 修改远程仓库地址:
>    > 1.直接修改
>    >    	git remote origin set-url [url]
>    > 2.先删除后增加
>    >    	git remote rm origin
>       git remote add origin [url]

### 创建远程分支,删除远程分支示例
> 1. 在本地创建新分支;
>    ![2345截图20180103150839.png](http://upload-images.jianshu.io/upload_images/122816-f66a2a133e39806b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 2. 在本地新分支上创建login.html
>    ![2345截图20180103151441.png](http://upload-images.jianshu.io/upload_images/122816-ef66a2a8b34dd917.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103151552.png](http://upload-images.jianshu.io/upload_images/122816-21313472a3858e64.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 3. 将本地分支提交到远程仓库,首先使用命令:git remote -v查看远程仓库的名称,默认为origin,接着提交本地分支到远程仓库
>    ![2345截图20180103152053.png](http://upload-images.jianshu.io/upload_images/122816-994ec0ff59e76ee4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103152205.png](http://upload-images.jianshu.io/upload_images/122816-5f53e2c7fbca96cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103152218.png](http://upload-images.jianshu.io/upload_images/122816-33751fe95466dfec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103152503.png](http://upload-images.jianshu.io/upload_images/122816-223f9a9ce6bf0744.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 4. 在GitHub使用图形化界面来合并远程分支
>    ![2345截图20180103152851.png](http://upload-images.jianshu.io/upload_images/122816-ead76648173494d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103153035.png](http://upload-images.jianshu.io/upload_images/122816-0f4dd3400e7a31ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103153144.png](http://upload-images.jianshu.io/upload_images/122816-95499cc5a45abd66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103153234.png](http://upload-images.jianshu.io/upload_images/122816-cb277f4eac84cf5d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 5. 将login文件合并到master分支并删除本地分支和远程分支
>    ![2345截图20180103155931.png](http://upload-images.jianshu.io/upload_images/122816-cd1ae87e9676bfba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103160018.png](http://upload-images.jianshu.io/upload_images/122816-b310a57d314d548b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180103160215.png](http://upload-images.jianshu.io/upload_images/122816-e83dfcc699252e3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Git-Tag(标签)主要命令
> 标签(Tag)可以针对某一时间点的版本做标记，常用于版本发布
> 切换标签: git checkout [tagname] 
> 用git show命令可以查看标签的版本信息：git show 标签名称
> 给指定的commit打标签:  git tag -a v0.1.1 9fbc3d0
> 将v0.1.2标签提交到git服务器:  git push origin v0.1.2 
> 将本地所有标签一次性提交到git服务器: git push origin –-tags
> 删除远程tag: git push :refs/tags/v0.1.2

### Git-Tag版本发布示例
>  1. 修改登录界面
>     ![2345截图20180104153751.png](http://upload-images.jianshu.io/upload_images/122816-1189084d32fb1c5c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  2. 提交到远程仓库,并将它作为V1.0版本
>     ![2345截图20180104155402.png](http://upload-images.jianshu.io/upload_images/122816-ec6bfd84973cdd9c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180104155528.png](http://upload-images.jianshu.io/upload_images/122816-964ddc8ac87d317b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180104155923.png](http://upload-images.jianshu.io/upload_images/122816-6b0e9409cf16de1a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180104160106.png](http://upload-images.jianshu.io/upload_images/122816-c711190f3be8fc31.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  3. 将本地标签提交到远程服务器
>     ![2345截图20180104160917.png](http://upload-images.jianshu.io/upload_images/122816-91cc0f1035e07318.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180104160956.png](http://upload-images.jianshu.io/upload_images/122816-9eb9825d4479ea9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  4. 删除本地标签和远程标签
>     ![2345截图20180104163038.png](http://upload-images.jianshu.io/upload_images/122816-18fba31d04285f8d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180104163320.png](http://upload-images.jianshu.io/upload_images/122816-f6b0d7c4dba08551.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>     ![2345截图20180104163350.png](http://upload-images.jianshu.io/upload_images/122816-a788b0a32bb30f29.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 多人合作开发创建团队
> ![Snip20180111_1.png](http://upload-images.jianshu.io/upload_images/122816-0f2f1461d1a714c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104165321.png](http://upload-images.jianshu.io/upload_images/122816-00b0c742136d2784.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104165505.png](http://upload-images.jianshu.io/upload_images/122816-f38a2e5355da4322.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104165615.png](http://upload-images.jianshu.io/upload_images/122816-724d8ad6edfebf14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104165914.png](http://upload-images.jianshu.io/upload_images/122816-c390503c23afe850.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 多人合作开发团队创建项目
> ![2345截图20180104165914.png](http://upload-images.jianshu.io/upload_images/122816-815d2965fbb14ba9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104171442.png](http://upload-images.jianshu.io/upload_images/122816-a86723e05ec90591.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104171518.png](http://upload-images.jianshu.io/upload_images/122816-9a931c8c1b2f8734.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104171716.png](http://upload-images.jianshu.io/upload_images/122816-42d34acf65d3b1d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 多人合作开发项目示例
> 1. 在A用户下创建index.html文件,并提交
>    ![2345截图20180104172607.png](http://upload-images.jianshu.io/upload_images/122816-303347d63f130ca1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104172714.png](http://upload-images.jianshu.io/upload_images/122816-07f38ca080ddae0a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 2. 由于当前组织下只有A用户,所以需要邀请另一个用户加入组织来共同开发项目
>    1) 首先进入组织
>    ![2345截图20180104173739.png](http://upload-images.jianshu.io/upload_images/122816-e7632add0319fe84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    2) 邀请
>    ![2345截图20180104173819.png](http://upload-images.jianshu.io/upload_images/122816-d74f2f3848333f73.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    3) 可以采用GitHub名字或这B用户注册GitHub邮箱来邀请
>    ![2345截图20180104174723.png](http://upload-images.jianshu.io/upload_images/122816-ad5e22504254b37e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104174822.png](http://upload-images.jianshu.io/upload_images/122816-0f81d4d20da2bc1b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104174845.png](http://upload-images.jianshu.io/upload_images/122816-33f98ee68c27d24e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    B用户的邮箱会收到类似以下图片的一封邮件
>    ![2345截图20180104175349.png](http://upload-images.jianshu.io/upload_images/122816-0482d4be14fc0a58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    B用户点击加入
>    ![2345截图20180104175853.png](http://upload-images.jianshu.io/upload_images/122816-ae017e0a1dbc5787.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104180144.png](http://upload-images.jianshu.io/upload_images/122816-a676df61a0b49d85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    A用户修改index.html文件,并提交到远程仓库
>    ![2345截图20180104182358.png](http://upload-images.jianshu.io/upload_images/122816-2d54500c6ab27d0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104182655.png](http://upload-images.jianshu.io/upload_images/122816-a2ffcbf7b286f911.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104182749.png](http://upload-images.jianshu.io/upload_images/122816-3198ffb4302dc668.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    B用户克隆代码,并修改代码提交远程仓库
>    ![2345截图20180104183129.png](http://upload-images.jianshu.io/upload_images/122816-58d4e2f8ee686717.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104183706.png](http://upload-images.jianshu.io/upload_images/122816-467d5e94ad37266b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104183932.png](http://upload-images.jianshu.io/upload_images/122816-89e273fffb01a0c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104184133.png](http://upload-images.jianshu.io/upload_images/122816-0d6e2abe290aa6c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104185020.png](http://upload-images.jianshu.io/upload_images/122816-dfb11e42931d00c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    这个是由于B用户没有权限所导致的,所以需要这个组织的所有者A用户来开通权限
>    ![2345截图20180104192240.png](http://upload-images.jianshu.io/upload_images/122816-7791f8521a22b319.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104192328.png](http://upload-images.jianshu.io/upload_images/122816-31dbc342bd9925ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104192557.png](http://upload-images.jianshu.io/upload_images/122816-a8fe9c380e5caf5c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104192729.png](http://upload-images.jianshu.io/upload_images/122816-e271a39bb4f0ba10.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104192755.png](http://upload-images.jianshu.io/upload_images/122816-080f99ab457e8074.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104192825.png](http://upload-images.jianshu.io/upload_images/122816-dbb7fed74ec3fb1e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104192922.png](http://upload-images.jianshu.io/upload_images/122816-ff5aaceee8f00f39.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193017.png](http://upload-images.jianshu.io/upload_images/122816-f2c2c51b46fd85e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193051.png](http://upload-images.jianshu.io/upload_images/122816-de0620d5ea63e8cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193127.png](http://upload-images.jianshu.io/upload_images/122816-f547a28e6687e219.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193302.png](http://upload-images.jianshu.io/upload_images/122816-934ad74b478de5bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193335.png](http://upload-images.jianshu.io/upload_images/122816-b9ebb22d81bf4c6f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193453.png](http://upload-images.jianshu.io/upload_images/122816-8d7673c0c0532346.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104193528.png](http://upload-images.jianshu.io/upload_images/122816-c45cf616796e7c45.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    B用户提交代码完成
>    ![2345截图20180104195027.png](http://upload-images.jianshu.io/upload_images/122816-e6bccfb248164a00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>    ![2345截图20180104195225.png](http://upload-images.jianshu.io/upload_images/122816-a21d72b119bce01b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### webStorm图形化界面使用Git
> ![2345截图20180104200030.png](http://upload-images.jianshu.io/upload_images/122816-4d81c7fe1517c9f8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104200234.png](http://upload-images.jianshu.io/upload_images/122816-3a5d878a2caa3479.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180104200433.png](http://upload-images.jianshu.io/upload_images/122816-54c36bf1ee43e581.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104200759.png](http://upload-images.jianshu.io/upload_images/122816-96bafd431b8795da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104200818.png](http://upload-images.jianshu.io/upload_images/122816-cfe09e9fd0b9efd6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104201042.png](http://upload-images.jianshu.io/upload_images/122816-5d595c04019fa3e2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104201203.png](http://upload-images.jianshu.io/upload_images/122816-08003c3be841fd3a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104201310.png](http://upload-images.jianshu.io/upload_images/122816-3bb3809991695c2c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104201352.png](http://upload-images.jianshu.io/upload_images/122816-191f5eb8c4d28d9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>  ![2345截图20180104201507.png](http://upload-images.jianshu.io/upload_images/122816-e37d406cce965823.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### OSChina提交代码示例
> OSChina是国内类似于GitHub的代码托管平台
> ![2345截图20180105144623.png](http://upload-images.jianshu.io/upload_images/122816-56a1aaf341f011f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105144641.png](http://upload-images.jianshu.io/upload_images/122816-23899ec788b5f0e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 去C:\Users\YDH\.ssh这个目录下找到公钥,放到OSChina上
> ![2345截图20180105144723.png](http://upload-images.jianshu.io/upload_images/122816-2beed98c1f6ebb84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105145414.png](http://upload-images.jianshu.io/upload_images/122816-349ca9f1775ae5e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105145713.png](http://upload-images.jianshu.io/upload_images/122816-a7416af416c9cf11.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105145836.png](http://upload-images.jianshu.io/upload_images/122816-cd993fcf5979e7f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105145949.png](http://upload-images.jianshu.io/upload_images/122816-4be0522b79d11c32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105150314.png](http://upload-images.jianshu.io/upload_images/122816-03742810e1456435.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> ![2345截图20180105150342.png](http://upload-images.jianshu.io/upload_images/122816-a2265a0499101b21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
