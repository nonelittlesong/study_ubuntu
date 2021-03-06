# study-ubuntu

参考：  
- https://github.com/junegunn/vim-plug  
  
**wiki**  
* [ssh](https://github.com/nonelittlesong/study-ubuntu/wiki/SSH)
* [git](https://github.com/nonelittlesong/study-ubuntu/wiki/git)
* [pip](https://github.com/nonelittlesong/study-ubuntu/wiki/pip)
* [labelimg](https://github.com/nonelittlesong/study-ubuntu/wiki/LabelImg)
* [ip设置](https://github.com/nonelittlesong/study-ubuntu/wiki/ip%E8%AE%BE%E7%BD%AE)
* [安装oh-my-zsh](https://github.com/nonelittlesong/study-ubuntu/wiki/install-oh-my-zsh)
* [Shell](https://github.com/nonelittlesong/study-ubuntu/wiki/Shell)
* [CentOS User and Group](https://github.com/nonelittlesong/study-ubuntu/wiki/CentOS-User-and-Group)
* [防火墙](https://github.com/nonelittlesong/study-ubuntu/wiki/Ubuntu16%E9%98%B2%E7%81%AB%E5%A2%99)

## 一、Shortcuts
* `ctrl+shift+t`:在原窗口打开终端
* `将窗体托向屏幕两侧实现分屏`
* `Ctrl+Super+D` 最小化所有窗口
* `Super` 显示快捷键

## 二、Commands
#### [查看处理器和系统架构](https://blog.csdn.net/wykkunkun/article/details/79675675)
```sh
uname -a; uname -m; dpkg --print-architecture； getconf LONG_BIT; file /sbin/init;
```
#### sed文件处理
```sh
sed -i '1,$d' result.txt
```

**查看端口**  
```sh
lsof -i:端口号
# 或者
netstat -tunlp |grep 端口号
```

**updatedb**  
更新slocate  

**dpkg -l**  
>第一个字符为期望值,它包括:  
>u 状态未知,这意味着软件包未安装,并且用户也未发出安装请求。  
>i 用户请求安装软件包。  
>r 用户请求卸载软件包。  
>p 用户请求清除软件包。  
>h 用户请求保持软件包版本锁定。  
>
>第二个字符是软件包的当前状态,它包括:  
>n 软件包未安装。  
>i 软件包安装并完成配置。  
>c 软件包以前安装过,现在删除了,但是它的配置文件还留在系统中。  
>u 软件包被解包,但还未配置。  
>f 试图配置软件包,但是失败了。  
>h 软件包安装,但是但是没有成功。  
>
>第三个字符是错误状态,有四种状态。第一种状态标识没有问题,为空。其它三种包括:  
>h 软件包被强制保持,因为有其它软件包依赖需求,无法升级。  
>r 软件包被破坏,可能需要重新安装才能正常使用(包括删除)。  
>x 软包件被破坏,并且被强制保持。  

**ls与find**  
ls 路径名+通配符 会显示路径名  
find得到完整路径名  

**进程**  
```
# 查看进程
$ ps -ef|grep mysqld
# 杀死进程
$ kill -9 进程号
```

**zip**  
```
$ zip -r target.zip files
```
**rename file**  
```
$ mv fromfilename tofilename
```
**卸载cmake**  
```
$ sudo apt-get remove cmake
```
>The following packages were automatically installed and are no longer required:  
&nbsp;&nbsp;cmake-data libjsoncpp1  
>Use 'sudo apt autoremove' to remove them.  

**查找文件**  
filename可以是文件名的一部分  
```
$ locate filename
```

## 三、Troubleshooting
**1、 版本更新后输入法出现问题**  
>（1） 打开设置  
>（2） 点击Manager Installed Languages  
>（3） Keyboard input method system:里面有Ibus,XIM(fcitx).none 三种输入架构，如果使用智能拼音就选Ibus，搜狗输入法的话就选XIM。  
>（4） 回到设置input source，选择中文输入法  
>（5） 重启电脑  

**2、 无法链接proxy**  
>(1) 打开preferences  
>(2) General  
>(3) Network Proxy  
>(4) check up proxy  

**3、 the channel bionic partner is unknown**  
用`sudo apt install flashplugin-installer`

**4、 sudo: unable to resolve host ubuntu: Connection timed out**  
原因：  
```
这种问题是由于：在系统盘 “etc “文件夹下面的hosts里面的主机名(localhost)和hostname里面的主机名不一致导致的。
```
解决办法：  
```
# 编辑 /etc/hosts 和 /etc/hostname，使主机名一致
```

## 四、[修改密码](https://blog.csdn.net/lxllinux/article/details/81910507)

1. 在 Grub 菜单选择 `Advanced Options for Ubuntu`。:warning: 如果开机时没有进入 Grub 菜单，则在开机时按住 <kbd>shift</kbd> 键。
2. 选择 `Recovery Mode`。
3. 选择 `root Drop to root shell prompt`。
4. 回车，进入命令行。
5. 执行 `passwd <username>` 重置密码。
