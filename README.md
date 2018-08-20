# linuxos-backup

## sudo apt-get install git

## apt-get 安装 nodejs

问题：
apt-get install libprotobuf-dev

下列软件包有未满足的依赖关系： 
libprotobuf-dev : 依赖: zlib1g-dev 但是它将不会被安装 
E: 无法修正错误，因为您要求某些软件包保持现状，就是它们破坏了软件包间的依赖关系。

原因：
Linux下经常需要安装不同类型的库，在Ubuntu中，这些类库都是以“lib_name-version”的形式命名的。很多库之间存在依赖关系，即要安装这个就必须安装那个。有时候，类库之间依赖关系无法满足，你所要安装的程序就不能安装。 
这类问题大多是由于相互依赖的几个库中一个或多个的版本已经更新，而用户要安装的库依赖于这几个库的较低的版本，这时候可以试试使用“sudo aptitude install ”（尖括号内为你要安装的程序的名字）

我这个问题就是因为

libprotobuf-dev : 依赖: zlib1g-dev ，但是zlib1g-dev依赖了一个旧的包。

使用sudo apt-get install zlib1g-dev，观察到

zlib1g-dev : 依赖: zlib1g (= 1:1.2.8.dfsg-2ubuntu4) 但是 1:1.2.8.dfsg-2ubuntu4.1 已安装。

解决办法：
使用aptitude

aptitude与 apt-get 一样，是 Debian 及其衍生系统中功能极其强大的包管理工具。与 apt-get 不同的是，aptitude在处理依赖问题上更佳一些。举例来说，aptitude在删除一个包时，会同时删除本身所依赖的包。这样，系统中不会残留无用的包，整个系统更为干净。

sudo aptitude install libprotobuf-dev

运行后，不接受未安装方案，接受降级方案。搞定 
这里写图片描述

最需要注意的是：
**如图所示，提示是否接受解决方案？？这里一定要选择N,否则就不成功，依旧出现依赖问题。 
其余部分选择Y**

唯一需要注意的问题是：
需要手动安装aptitude命令

sudo apt install aptitude


1、先在系统上安装好nodejs和npm

sudo    apt-get    install    nodejs-legacy

sudo    apt-get    install    npm

2、安装用于安装nodejs的模块n

sudo    npm    install    -g    n

3、通过n模块安装指定的nodejs

sudo    n    latest

sudo    n    stable

sudo    n    lts

4、升级npm为最新版本

sudo    npm    install    npm@latest    -g

5、查看版本

sudo    node    -v

sudo    npm    -v

作者：WayD_ec7c
链接：https://www.jianshu.com/p/f2592d106aac
來源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。



