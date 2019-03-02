

# Swift Perfect 部署至阿里云 Ubuntu 服务器上

环境：

​	Ubutun 16.04, Swift 4.2.2

> 闲话就不多说了，直接上步骤吧！需要注意的地方，我再多逼逼几句。



1、 购买阿里云轻服务器

2、**安装 Swift Tool Chain**

> **这里就要开始逼逼了！**
>
> 1. 利用 ssh 等录至阿里云服务器
>
>    终端输入命令：ssh root@192.168.0.1(此处替换为你的阿里云真实IP)
>
>    然后就是输入密码，再然后就可以登录至阿里云服务器了
>
> 2. 下载 Swift Tool Chain 
>
>    终端输入命令：curl https://swift.org/builds/swift-4.2.2-release/ubuntu1604/swift-4.2.2-RELEASE/swift-4.2.2-RELEASE-ubuntu16.04.tar.gz -o swift-4.2.2-RELEASE-ubuntu16.04.tar.gz
>
> 3. 安装 Swift Tool Chain
>
>    终端输入命令：tar xzf swift-4.2.2-RELEASE-ubuntu16.04.tar.gz -o swift-4.2.2-RELEASE-ubuntu16.04.tar.gz （解压下载好的安装包）
>
> 4. 配置环境
>
>    终端输入命令：export PATH=/(安装包的绝对路径):"${PATH}"
>
> 5. 安装 PGP Key
>
>    终端输入命令（全部拷贝至终端回车）：
>
>    ```shell
>    gpg --keyserver hkp://pool.sks-keyservers.net \
>          --recv-keys \
>          '7463 A81A 4B2E EA1B 551F  FBCF D441 C977 412B 37AD' \
>          '1BE1 E29A 084C B305 F397  D62A 9F59 7F4D 21A5 6D5F' \
>          'A3BA FD35 56A5 9079 C068  94BD 63BC 1CFE 91D3 06C6' \
>          '5E4D F843 FB06 5D7F 7E24  FBA2 EF54 30F0 71E1 B235' \
>          '8513 444E 2DA3 6B7C 1659  AF4D 7638 F1FB 2B2B 08C4'
>    ```
>
> 6. 验证
>
>    终端输入命令：swift --version
>
>    如果出现以下信息表示安装成功
>
>    ```shell
>    Swift version 4.2.2 (swift-4.2.2-RELEASE)
>    Target: x86_64-unknown-linux-gnu
>    ```

3、 安装依赖库

> 安装依赖库基本可以直接使用 apt-get install xxxx 命令进行安装，但是首次使用时可能会遇到 404 问题（找不到对应的镜像），这时需要更新apt的源。
>
> 更新源
>
> ```shell
> sudo apt-get update
> ```
>
> 安装 Perfect 依赖 OpenSSL、libssl-dev和uuid-dev
>
> ```shell
> sudo apt-get install openssl libssl-dev uuid-dev
> ```
>
> 安装 git
>
> ```shell
> sudo apt-get install git
> ```
>
> 安装 MySQL
>
> ```shell
> sudo apt-get install mysql-server
> sudo apt-get install mysql-client
> # 安装 MySQL 文件
> sudo apt-get install libmysqlclient-dev -y 
> ```



5、运行 Perfect 

> 从 Perfect git 仓库 clong 源代码（提示，请创建好自己的文件夹）
>
> ```shell
> #克隆代码
> git clone https://github.com/PerfectlySoft/PerfectTemplate.git
> # 进入到模板项目内部
> cd PerfectTemplate
> # 编译
> swift build
> # 运行
> .build/debug/PerfectTemplate
> ```

<h1><a href='../README.md'>返回列表</a> </h1>