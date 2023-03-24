

网页文档 网页文档 网页文档！！！
===================================
第一章 VMware虚拟机软件安装
--------
1.1 VMware软件的下载与购买::
1.2 VMware软件的安装
第二章 加载已有ubuntu开发环境
--------
第三章 搭建新的ubuntu开发环境
--------
3.1 ubuntu系统搭建	- 13 -
3.1.1 创建ubuntu虚拟机	- 13 -
3.1.2 系统安装	- 21 -
3.1.3 Ubuntu的基本配置	- 28 -
3.1.4 Ubuntu的网络设置	- 32 -
3.1.5 U盘的加载	- 36 -
3.1.6 虚拟机基本库安装	- 37 -
3.1.7编译OK3568 Linux源码必要库安装	- 37 -
3.2 Qt Creator安装	- 37 -
第四章 相关代码编译
--------
4.1编译前准备	- 43 -
4.1.1 环境说明	- 43 -
4.1.2 拷贝源码	- 43 -
4.2 内核编译	- 43 -
4.2.1 全编译测试	- 43 -
4.2.2 单独编译测试	- 44 -
4.2.3 清除编译生成的文件	- 45 -
4.3 Image文件的使用	- 46 -
4.4 Qt Creator环境配置	- 46 -
4.4.1 交叉编译器配置	- 46 -
4.4.2 Qt Versions 配置	- 47 -
4.4.3 Kits 配置	- 48 -
4.5 应用程序编译及运行	- 48 -
4.5.1 编译并运行命令行应用	- 48 -
4.5.2 编译并运行QT应用程序	- 49 -

第一章 VMware虚拟机软件安装
本章主要介绍VMware虚拟机的安装，以VMware workstation 15 Pro v15.1.0为例展示操作系统的安装配置过程。
1.1 VMware软件的下载与购买
登陆VMware官网https://www.vmware.com/cn.html下载Workstation Pro并获取产品密匙。VMware是付费软件，需要自行购买，或者使用VMware提供的试用版本。

等待下载完成后双击启动文件启动安装程序。
1.2 VMware软件的安装
双击启动程序进入安装向导。

点击“下一步”。

勾选我接受许可协议中的条款，点击“下一步”。

修改安装位置，装到自己电脑安装软件的分区，点击“下一步”。

勾选，点击“下一步”。

勾选添加快捷方式，点击“下一步”。

点击“安装”。

等待安装完成。

点击完成后可进行试用。若用户需要长期使用，需要到官方购买，填写许可证。

第二章 加载已有ubuntu开发环境
注意：
建议初学者直接使用飞凌搭建好的虚拟机环境，环境中已经安装好交叉编译器和Qt环境。了解完该章节后可以直接跳转到编译章节。
提供开发环境的账户为：forlinx，密码为：forlinx

在VMware下使用虚拟机的环境有两种方式，一种是直接加载已有的环境，另一种是新建一个环境，我们先来说说如何加载一个已经存在的环境。
首先，下载飞凌提供的开发环境，开发环境资料中有MD5校验文件，用户下载完开发环境资料，先对开发环境压缩包进行MD5校验（MD5校验可以在网络上选择MD5在线工具校验，也可以下载MD5校验工具进行校验，可根据实际情况选择），查看校验码和校验文件中校验码是否一致，若一致则下载文件正常；若不一致，则文件可能有破损，需要重新下载。
选中压缩包一起解压

解压完成后出现 3568标准环境文件夹，其中.vmx为虚拟机要打开的文件。




打开虚拟机，选择解压出来的3568.vmx

加载完成后点击开启此虚拟机，即可运行，进入系统的界面。


	提供开发环境的账户为forlinx，密码为forlinx，填好密码后选择Sign in登录。



第三章 搭建新的ubuntu开发环境
注意：初学者不建议自己搭建系统，建议使用已有虚拟机环境，不需要搭建环境的此节可以跳过本章节主要讲解了ubuntu系统的搭建过程。
3.1 ubuntu系统搭建
3.1.1 创建ubuntu虚拟机
打开VMware软件，点击创建新的虚拟机。进入以下界面：

选择自定义，点击“下一步”。

选择对应VMware版本的兼容性，版本可在帮助->关于VMware Workstation中查看，点击“下一步”。

选择稍后安装操作系统，点击“下一步”。

保持默认，点击“下一步”。

修改虚拟机名称及安装位置，点击“下一步”。

按照实际情况设置处理器数量。

同样按照实际情况设置内存大小。

设置网络类型，默认为NAT模式，点击下一步。后面的步骤保持默认值，直到指定磁盘容量步骤。

IO控制器类型这里默认选择LSI就可以：

这里同样是默认选择SCSI。

这里选择创建新的虚拟磁盘：

设置磁盘大小为200G，并选择磁盘的存在形式，然后点击“下一步”完成。
   
指定磁盘文件，这里默认即可。

默认点击“完成”即可。


至此，虚拟机创建完成。
下一小节中我们介绍Ubuntu系统在虚拟机中的安装，其在真机中的安装方法与虚拟机类似。这里我们介绍在虚拟机中安装Ubuntu系统的方法。


3.1.2 系统安装
我们选择安装的Ubuntu 版本是18.04，首先去Ubuntu官网获取Ubuntu18.04 64位镜像，下载地址为：http://sources.ubuntu.com/18.04/下载“ubuntu-18.04.5-desktop-amd64.iso”这个版本。

右击刚创建完成的Ubuntu64位 在弹出菜单中选择设置：

弹出“虚拟机设置菜单”根据如下图： 

点击CD/DVD（SATA），选择使用ISO映像文件，浏览选择前面下载的Ubuntu镜像，然后确定。

设置好镜像后，保证网络可用，然后开启虚拟机，进行Ubuntu镜像的安装。

开启虚拟机后，等待出现安装界面如下：

如图左侧选择语言后,点击“Install  Ubuntu”后弹出选择语言界面。Ubuntu默认语言是英文的，当然，也可以选择中文，默认选择的语言在后期也是可以重新设置的，选择完成后continue。

接下来，默认选择continue继续安装，安装过程会很慢，然后点击“continue”：

默认，点击Install Now，会弹出下图，点击“continue”即可。


接下来选择时区，这里点击上海时区或输入Shanghai即可（不同时区根据实际情况选择即可），点击“继续”。最后设置用户名和密码，点击“continue”就会自动安装：

安装过程下图，网络不好可以Skip跳过，不影响安装。

安装完成后显示如下图，点击“Restart Now”重启（或者点击“重新启动客户机”）：


重启完成需要使用用户名和密码登录，登录后系统界面如下图：


以上，将虚拟机关机后，将CD设置恢复，按照下图配置，点击确定，然后重新打开虚拟机，看能否正常启动Ubuntu。

3.1.3 Ubuntu的基本配置
安装好Ubuntu18.04操作系统后，要进行一些配置。
VMware Tools安装：
接下来安装VMware Tools，如果不安装该工具，在Windows主机和虚拟机之间无法使用复制粘贴、文件拖拽。首先点击VMware 导航栏上的“虚拟机”，然后在下拉框中点击“安装VMware Tools”：

完成后进入Ubuntu，桌面会出现VMware Tools的光盘图标，点击进入其中：

双击VMwareTools图标，进入后看到一个压缩文件VMwareTools-10.3.10-12406962.tar.gz（不同的虚拟机版本可能会不同），


复制文件到主目录下面（即home 个人用户名的目录下）：


按键盘【Ctrl+Alt+T】调出终端命令界面，使用tar命令对VMwareTools安装包解压（使用sudo命令会提示输入密码，根据提示直接输入密码回车即可，Linux系统密码输入无回显，确保输入的密码正确后按回车确认即可）：
forlinx@ubuntu:~$ sudo tar -xvf VMwareTools-10.3.10-12406962.tar.gz 
[sudo] password for forlinx:
执行完解压命令后，使用ls查看，会出现一个vmware-tools-distrib的文件目录， 进入到该目录
forlinx@ubuntu:~$ ls
Desktop   examples.desktop   nfs   snap   tftp   VMwareTools-10.3.10-12406962.tar.gz  vmware-tools-distrib   work
forlinx@ubuntu:~$ cd vmware-tools-distrib/	                      //使用cd命令进入该目录
forlinx@ubuntu:~/vmware-tools-distrib$ ls                         //查看该目录下的文件
bin   caf   doc   etc   FILES   INSTALL   installer   lib   vgauth   vmware-install.pl
在当前目录下，输入sudo ./vmware-install.pl，进行安装，回车后输入密码，然后就开始安装，遇到[yes]/[no]就输入yes，其他一律回车默认安装就可以。
forlinx@ubuntu:~/vmware-tools-distrib$ sudo ./vmware-install.pl 
[sudo] password for forlinx: 		     //输入forlinx账户的密码，无回显，无法看到输入内容
安装过程信息较长，此处省略
open-vm-tools packages are available from the OS vendor and VMware recommends 
using open-vm-tools packages. See http://kb.vmware.com/kb/2073803 for more 
information.
Do you still want to proceed with this installation? [no] yes			//输入yes
... ...		

VMware tools工具完成后，可以实现Windows和Ubuntu之间的文件复制粘贴，虚拟机自适应全显等功能。如果虚拟机不能够全屏显示，可以通过点击查看，选择自动调整大小，点击自动适应客户机，即可实现虚拟的全屏问题，VMware tools安装成功。

基本设置：
在下图位置进行大部分的系统设置。Ubuntu上很多设置的需求都可以在这里完成。

3.1.4 Ubuntu的网络设置
NAT模式
在使用网络前，先确保我们的虚拟机能连接互联网，打开虚拟机设置，网络适配器中的网络桥接模式改为“NAT模式”：

在虚拟机中，VMware虚拟网卡设置为NAT模式时，Ubuntu环境中网络设置为动态IP即可。在这种模式下虚拟NAT设备和主机网卡相连通。这是我们虚拟机上外网最常用的方式。


网络设置为动态ip。

桥接模式：
如果在使用TFTP，SFTP等服务器时则需要设置虚拟机的网络联系方式为桥接方式。VMware虚拟网卡设置为桥接模式时，主机网卡和虚拟机网卡通过虚拟网桥进行通信，需要将Ubuntu的IP与主机IP设置在同一个网段。



 	设置静态ip，此时Ubuntu的IP与主机IP需设置在同一个网段。


注意：网络设置部分涉及到的IP以及DNS请按照用户自身的实际环境来设置，手册为举例说明。
3.1.5 U盘的加载
打开虚拟机设置，USB控制器，在兼容性里面选择USB3.0，然后确定。如下图，因为目前大多数电脑都支持USB3.0的接口，如果不设置，当我们插入USB3.0接口，是不能连接到虚拟机的。如下图：

虚拟机启动后，插入U盘，虚拟机右下角会多出一个类似“U盘”的图标，右击-->连接即可，然后就可以在文件系统看到多一个目录，说明U盘加载成功，如图：


3.1.6 虚拟机基本库安装
在进行开发之前，还需要一些其他的必要库，我们使用以下命令逐一安装，安装前需保证网络可正常使用，能上外网：
forlinx@ubuntu:~$ sudo apt-get update                        //更新下载源信息
forlinx@ubuntu:~$ sudo apt-get install build-essential            //提供编译程序必须软件包的列表信息
forlinx@ubuntu:~$ sudo apt-get install libncurses*               //用于生成基于文本的用户界面
forlinx@ubuntu:~$ sudo apt-get install lzop                     //基于Lzo库的压缩解压工具
forlinx@ubuntu:~$ sudo apt-get install net-tools                 //网络配置工具
3.1.7编译OK3568 Linux源码必要库安装
forlinx@ubuntu:~$ sudo apt-get update                                       //更新apt-get下载源
forlinx@ubuntu:~$ sudo apt-get install openssh-server vim git fakeroot           //必备工具包的安装
forlinx@ubuntu:~$ sudo apt-get install repo git ssh make gcc libssl-dev liblz4-tool expect g++ patchelf chrpath gawk texinfo chrpath diffstat binfmt-support qemu-user-static live-build bison flex fakeroot cmake gcc-multilib g++-multilib unzip device-tree-compiler python-pip libncurses5-dev
这些库文件是自行搭建3568 Linux编译环境时，准备编译Linux源码需要下载的库文件，若不是搭建OK3568 Linux开发环境，可跳过此步骤。
3.2 Qt Creator安装
将qt-creator-opensource-linux-x86_64-4.1.0.run拷贝至当前用户家目录下的任意目录下，执行下面命令。
路径：OK3568-C（Linux）用户资料\Linux\源码\qt-creator-opensource-linux-x86_64-4.7.0.run
forlinx@ubuntu:~$ ./qt-creator-opensource-linux-x86_64-4.7.0.run                   

然后会弹出图形界面的安装窗口，按照提示进行安装：
		 
 	
在线安装的用户需要自己注册测Qt账户，已有Qt账户的直接登录即可，Qt密码要求为：包含大写字母、小写字母、数字，注册登陆成功后，点击next。
离线安装的用户点击跳过即可。


点击next

用户可根据自己习惯设置安装路径，这边直接默认，点击next

完全安装，点击next


点击install，等待安装完成。

安装完成，点击finish。这时将自动打开Qt界面，也可以通过命令行启动，执行以下命令，以后台方式打开Qt Creator，用户打开时以自己实际安装路径为准：
forlinx@ubuntu:~$ cd /home/forlinx/qtcreator-4.7.0/bin
forlinx@ubuntu:~$ ./qtcreator &

出现Qt Creator工具界面。Qt Creator安装完毕。


第四章 相关代码编译
本章节主要描述开发板相关源码的编译方法，包括内核源码编译、应用程序编译方法。
4.1编译前准备
4.1.1 环境说明
开发环境操作系统：Ubuntu18.04  64位版
交叉工具链：aarch64-linux-gnu
开发板使用Bootloader 版本：u-boot-2017.09
开发板内核版本：linux-4.19.206
开发板移植QT版本：qt5.14.2
4.1.2 拷贝源码 
程序源码：用户资料\Linux\源码\OK3568-linux-source.tar.bz2
创建工作目录
forlinx@ubuntu:~$ mkdir -p /home/forlinx/3568							//按照顺序创建工作目录
将用户资料中的源码文件OK3568-linux-source.tar.bz2.a*拷贝到虚拟机/home/forlinx/3568目录。
forlinx@ubuntu:~$ cd /home/forlinx/3568									//切换到工作目录
forlinx@ubuntu:~/3568$ cat OK3568-linux-source.tar.bz2.a* > OK3568-linux-source.tar.bz2
forlinx@ubuntu:~/3568$ tar -xvf OK3568-linux-source.tar.bz2				//在当然位置解压压缩包
运行命令后等待完成即可。
4.2 内核编译
注意：
初次解压内核源码后，需要先对源码进行整体编译
整体编译过后，可根据实际情况再进行单独编译
该源码编译需要开发环境运行内存8G及以上，请不要修改我们提供的VM虚拟机镜像配置
4.2.1 全编译测试
在源码路径内，提供了编译脚本build.sh，运行该脚本对整个源码进行编译，需要在终端切换到解压出来的源码路径，找到build.sh文件
forlinx@ubuntu:~$ cd /home/forlinx/3568/OK3568-linux-source
以下操作需要在源码目录下操作，编译内核方法：
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh
执行后会有选项输入，如下图，输入1后按回车继续。
注意：若没有出现下述提示选项，则已完成配置，可以正常编译完成即可，不是必须项。

编译一段时间后会弹出下图界面，需要选择，提取图中信息，VCCIO4和VCCIO6选择1800000，其余的选择3300000，使用上↑下↓方向按键选择选项，按回车Enter确认选择即可。

注意：编译过程中报错如下：

解决方法：重新执行./build.sh命令，重新配置电压域，VCCIO4和VCCIO6选择1800000，其余的选择3300000，使用上↑下↓方向按键选择选项，按回车Enter确认选择即可。
注意：编译过程中卡顿在此处为正常现象，请不要终止编译。

注意：编译过程中报错如下：


解决方法：删除/OK3568-linux-source/buildroot/output/OK3568/build/qt5webengine-5.14.2文件夹。关闭虚拟机，重新配置虚拟机为8G内存，处理器数量为4，每个处理器的内核数量为1。开启虚拟机，重新执行./build.sh全编译命令。
最终的编译效果如下图：


编译成功后，将在/OK3568-linux-source/Image文件夹下生成对应编译工程结果文件，找到其中的镜像文件。

注意：update.img为打包好用于OTG或者TF卡完全烧写用，其它文件为分步烧写使用
4.2.2 单独编译测试
进行单独编译前需进行过全编译，在内核源码路径下进行操作。 
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh uboot        //单独编译uboot
//生成uboot.img，生成路径为/OK3568-linux-source/u-boot/uboot.img
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh kernel        //单独编译内核
//生成boot.img，生成路径为/OK3568-linux-source/kernel/boot.img
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh buildroot      //单独编译文件系统
//生成rootfs.ext2，生成路径为/OK3568-linux-source/buildroot/output/OK3568/image/rootfs.ext2
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh updateimg    //单独生成update.img
//使用上述路径的uboot.img boot.img rootfs.ext2 生成update.img 路径为 rockdev/update.img

编译成功后update.img里的内核不更新。请分步烧写/OK3568-linux-source/kernel/boot.img文件，分步烧写步骤请参考用户使用手册5.1.3 OTG分步烧写测试章节。
注意：用户图形界面配置修改过内核配置后，例如增加usb转串口ch340驱动，执行./build.sh kernel，烧写boot.img镜像，启动开发板后发现图形配置未生效，可以使用其中一个方法解决：

方法1：直接将配置写到内核默认配置文件/OK3568-linux-source/kernel/arch/arm64/configs/OK3568-C-
linux_defconfig中：
CONFIG_USB_SERIAL_CH341=y
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh kernel
方法2：注释掉/OK3568-linux-source/build.sh下图命令，如下图。
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh kernel

注意：用户图形界面配置修改过buildroot配置后，例如增加python3支持，执行./build.sh buildroot，烧写rootfs.ext2镜像，启动开发板后发现图形配置未生效，可以使用其中一个方法解决：
方法1：将图形界面配置完buildroot后，
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh buildroot
编译过程中弹出以下提示：
Found old config, override it? (y/n):y选择y，表示覆盖掉之前的.config文件。

方法2：直接将配置写到buildroot默认配置文件/OK3568-linux-source/buildroot/configs中：
BR2_PACKAGE_PYTHON3=y	
BR2_PACKAGE_PYTHON3_PY_PYC=y
forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh buildroot
编译过程中弹出以下提示： 
Found old config, override it? (y/n):n选择n，不要覆盖之前的.config文件。
4.2.3 清除编译生成的文件
注意：clenall命令会删除uboot文件夹内的中间文件和全编译生成的文件，使用前请修改build.sh脚本,将uboot部分注释掉，我们的uboot做了不开源处理，中间文件丢失会导致无法全编译。
用户在内核源码路径下进行操作。 
forlinx@ubuntu: ~/3568/OK3568-linux-source$ vi build.sh

forlinx@ubuntu: ~/3568/OK3568-linux-source$./build.sh cleanall

该操作清除所有中间文件。但不影响源文件，包括已经有改动的源文件。
4.3 Image文件的使用
update.img为打包好用于OTG或者TF卡完全烧写用，其它文件为分步烧写使用。单独编译生成的Image文件不会在update.img文件中更新，需使用单步烧写来烧录（详见用户使用手册OTG烧写）。
4.4 Qt Creator环境配置
Qt是跨平台的图形开发库，支持众多操作系统，在进行编译前需要对Qt Creator的编译环境进行配置。
4.4.1 交叉编译器配置
注意：Qt Creator所用的交叉编译器所在路径需全编译源码后生成，为了使用方便，我们在/OK3568-C（Linux）用户资料/工具目录下放置了host.tar压缩包，使用我们的开发环境创建绝对路径如下：
/home/forlinx/3568/OK3568-linux-source/buildroot/output/OK3568 将host.tar解压到该路径后继续本章节的操作。强烈建议全编译源码后再进行本章节操作。
1、点击Qt Creator 的Tools ->Options->Kits->Compilers， 然后点击Add ->GCC->C；
2、Name输入GCC；
3、Compiler Path点击Browse 选择交叉编译器的路径为：aarch64-linux-gcc和aarch64-linux-g++，如下图所示：
路径：OK3568-linux-source/buildroot/output/OK3568/host/bin
注意：buildroot下output目录需要源码经过全编译后才可生成。

4、按照同样的方法添加GCC编译器，点击右侧“Add->GCC->C++”，如图所示：

4.4.2 Qt Versions 配置
1、点击Qt Creator 的Tools ->Options->Qt Versions， 
2、然后点击Add，弹出对话框选择OK3568-linux-source/buildroot/output/OK3568/host/bin/qmake
3、点击open添加。

4、然后会返回 Qt Version配置框，Version name可以自行更改。
5、然后点击Apply及OK。
4.4.3 Kits 配置
Kits是一个构建套件，用来构建和选择开发编译环境，对于有多种QT库的项目很有用。将之前添加的交叉编译器和QT Version添加到Kits中，构建适合开发板的编译环境。
1、点击Qt Creator 的Tools ->Options->Kits， 然后点击Add，出现配置部分。
2、Name自行更改。
3、Compiler选择GCC。
4、Qt version选择Qt version创建时输入的名字。

6、然后点击Apply及OK。
4.5 应用程序编译及运行
4.5.1 编译并运行命令行应用
本小节使用看门狗测试程序，默认程序拷贝到/home/forlinx/3568目录。 
1、使用cd命令进入/home/forlinx/work目录
forlinx@ubuntu:~$ cd /home/forlinx/3568/OK3568-linux-source/app/forlinx/forlinx_cmd/fltest_watchdog
2、添加交叉编译器路径，使用make进行交叉编译
forlinx@ubuntu: ~/3568/OK3568-linux-source/app/forlinx/forlinx_cmd/fltest_watchdog$ export PATH=/home/forlinx/3568/OK3568-linux-source/buildroot/output/OK3568/host/bin/:$PATH
forlinx@ubuntu: ~/3568/OK3568-linux-source/app/forlinx/forlinx_cmd/fltest_watchdog$ make	
aarch64-linux-gcc watchdog.c -o fltest_watchdog  
generate fltest_watchdog success!!!
用file命令查看生成的文件信息
forlinx@ubuntu:~/3568/OK3568-linux-source/app/forlinx/forlinx_cmd/fltest_watchdog$ 
file fltest_watchdog 
fltest_watchdog: ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, for GNU/Linux 3.7.0, not stripped
通过结果可以看到编译生成的是64位、ARM的文件。
3、将编译生成的fltest_watchdog通过U盘或者ftp等方式拷贝到板子上，比如/forlinx路径下，下述以tf卡为例，拷贝到开发板，运行测试。
[root@ok3568:/]# cp /run/media/mmcblk1p1/fltest_watchdog /home/forlinx
[root@ok3568:/]# cd /home/forlinx
[root@ok3568:/home/forlinx]# ./fltest_watchdog
Watchdog Ticking Away!
4、参考用户使用手册“看门狗测试”章节测试。
4.5.2 编译并运行QT应用程序
在开发环境打开Qt Creator（用户根据自己的实际路径打开），点击Qt Creator 的File->Open File or Project，弹出窗口，选择/3568/OK3568-linux-source/app/forlinx/forlinx_qt/watchdog/watchdog.pro

打开项目后界面如下：（若没有自动改变页面，请按照截图所示选择）。

点击Configure Project后将适配本手册《Qt Creator环境配置》章节中构建的编译环境。
选择后界面如下：

点击Build->Clean All进行清空。（如果没有清除中间文件可以手动删除）。
点击Projects 取消选中Shadow build。

然后点击Build->Build All进行编译。

右下角Build进度条走完之后代表编译完成，此时在路径/app/forlinx/forlinx_qt/watchdog目录下会看到新生成的二进制文件fltest_qt_watchdog，如下：

将编译生成的可执行文件通过U盘或者ftp等方式拷贝到板子上，拷贝到开发板，运行测试即可。

声明
本手册版权归保定飞凌嵌入式技术有限公司所有。未经本公司的书面许可，任何单位和个人无权以任何形式复制、传播、转载本手册的任何部分，违者将被追究法律责任。

保定飞凌嵌入式有限公司所提供的所有服务内容旨在协助用户加速产品的研发进度，在服务过程中所提供的任何程序、文档、测试结果、方案、支持等资料和信息，都仅供参考，用户有权不使用或自行参考修改，本公司不提供任何的完整性、可靠性等保证，若在用户使用过程中因任何原因造成的特别的、偶然的或间接的损失，本公司不承担任何责任。	

更多帮助
注意事项与维护
-请勿带电插拔核心板及外围模块！
-请遵循所有标注在产品上的警示和指引信息。
-请保持本产品干燥。如果不慎被任何液体泼溅或浸润，请立刻断电并充分晾干。
-使用中注意本产品的通风散热，避免温度过高造成元器件损坏。
-请勿在多尘、脏乱的环境中使用或存放本产品。
-请勿将本产品应用在冷热交替环境中，避免结露损坏元器件。
-请勿粗暴对待本产品，跌落、敲打或剧烈晃动都可能损坏线路及元器件。
-请勿使用有机溶剂或腐蚀性液体清洗本产品。
-请勿自行修理、拆卸本公司产品，如产品出现故障请及时联系本公司进行维修。
-擅自修改或使用未经授权的配件可能损坏本产品，由此造成的损坏将不予以保修。

资料的更新
产品相关资料会不断的完善更新，本手册内容亦然如此；当您在使用这些内容时，请确保其为最新状态。
飞凌嵌入式产品资料更新通知采用微信公众号推送，敬请关注！
		资料获取
1.请登录飞凌官方论坛“bbs.witech.com.cn”→“开发板资料下载”选择对应平台下载；
2.下载前请阅读《资料下载说明》：http://bbs.witech.com.cn/thread-67932-1-1.html。


售后服务政策
1.如产品使用过程中出现硬件故障可根据售后服务政策进行维修；
2.服务政策：参见官方网站www.forlinx.com售后服务说明。
		送修地址
1.地 址：河北省保定市高开区向阳北大街2699号飞凌嵌入式技术有限公司新楼五层售后维修部
2.联系人：售后维修部
3.电 话：0312-3102650-952、953     
4.邮编：071000
5.邮寄须知：建议使用顺丰、圆通或韵达，且不接收任何到付。

技术支持范围
1. 本公司产品的软、硬件资源提供情况咨询；
2. 本公司产品的软、硬件手册使用过程中遇到的问题。
		技术讨论范围
1.源码的修改以及理解；
2.操作系统如何移植；
3.用户自行修改以及开发中遇到的软硬件问题；
注：以上三点虽不属于技术支持范围，但我公司会尽力为用户提供帮助，如仍然没能解决敬请谅解。
		
技术支持方式：
1. 电话：0312-3119192 
2. 论坛：bbs.witech.com.cn
3. 邮箱：
   Linux技术支持：  linux@forlinx.com
   Android技术支持： android@forlinx.com
   硬件技术支持： hardware@forlinx.com
4. 知识库：bbs.witech.com.cn/kb		
技术支持时间：
1.周一至周五：上午 9:00—11:30；下午 13:30—17:00；
2.公司按照国家法定节假日安排休息，在此期间无法提供技术支持，请将问题发送至邮箱或论坛技术支持区，我们会在工作日尽快给您回复。



