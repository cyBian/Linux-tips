# Linux tips

### Ubantu 系统

#### 重启网络 ``sudo service network-manager restart``

#### root用户和user用户相互切换

   从user切换到root用户

   ```shell
   sudo su
   ```

   从root切换回user

   ```shell
   su username
   ```

   或者直接输入``exit``，也可以<kbd>Ctrl</kbd>+<kbd>D</kbd> 组合键退出

#### SCP 命令
1. 从本地复制到远程
```
scp local_file remote_username@remote_ip:remote_folder
scp local_file remote_username@remote_ip:remote_file
scp local_file remote_ip:remote_folder
scp local_file remote_ip:remote_file
```
> 其中1,2两个命令指定了用户名，命令执行后需要输入密码；第一个仅指定了远程的目录，文件名不变，第2个指定了文件名
> 3,4两行命令没有指定用户名，命令执行后需要输入用户名和密码，第3个仅指定了远程的目录，文件名不变，第4个指定了文件名

2. 从远程复制到本地

只需将从本地复制到远程的命令的后两个参数调换顺序即可

```
scp remote_username@remote_ip:remote_file local_file
```
#### ubuntu 桌面假死鼠标点击无反应
1. 通过 ``ctrl + alt + F1``， 启动本地终端，切换到字符界面tty1
2. 查询进程，得到tty7的pid号：``ps -e|grep tty7`` 或者 ```ps -t tty7`
3. 切换至root用户``sudo su``，杀死tty7的进程``kill 9 <pid>``，重新回到登录界面，输入用户名密码回到正常图形界面


### Vim

### Shell 操作

+ 解决每次进入shell都要``source ~/.bashrc``问题
shell 下输入，编辑.bash_profile文件
``vim ~/.bash_profile``
在文件内部输入
​```shell
if test -f .bashrc ;then
source .bashrc
fi
```
``:wq``保存退出，重新启动shell使配置生效

+ Linux 解压tar.gz
``tar -zxvf filename.tar.gz``
```