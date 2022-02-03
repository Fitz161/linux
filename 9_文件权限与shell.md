![](pics9/file.jpg)

## 可执行文件
分为程序文件（二进制的CPU指令集合，可被加载运行）和脚本文件
![](pics9/bash.jpg)

## 目录的权限
无读权限，则目录表不允许读取，ls失败  
目录表记录文件名和inode关系，若无写权限，则不能更改文件名，创建，删除文件，但目录下的文件仍是可操作的
![](pics9/dir.jpg)
![](pics9/sticky.jpg)
stricky目录仅拥有者可删除文件，其他用户即使有目录写权限也不能删除文件
![](pics9/tmp.jpg)
t表示这是个sticky粘着目录

## 权限验证顺序
![](pics9/file2.jpg)
>文件主与进程主相同，则使用文件主权限，不查其他权限  
文件主与进程主不同，但同组，则使用组权限，不查其他权限  
否则其他用户权限<br>
root 用户不受权限制约

## ls
ls -l 长格式显示
ls -ld 显示文件夹的信息

## chmod
CHange the permission MODe of a file
![](pics9/chmod.jpg)
+-分别代表添加减少权限
![](pics9/chmod2.jpg)
![](pics9/chmod3.jpg)

## umask
控制文件/目录初始权限
![](pics9/umask.jpg)
umask 022 （-000 010 010 ）新创建文件中禁止组和其他用户的写权限
umask a=rwx file所有用户允许全部权限，同chmod 777 file
### SUID权限
chmod u+x file 之后文件允许其他人操作，但这种访问依赖于文件主提供的程序，进行有限的访问

# shell
shell 外壳
kernel 内核
Linux上标准shell：/bin/bash
![](pics9/shell.jpg)
![](pics9/shell2.jpg)
![](pics9/shell3.jpg)
![](pics9/shell4.jpg)
![](pics9/shell5.jpg)

## 启动bash
![](pics9/shell6.jpg)
>注册shell：系统登陆成功后，将shell注册成bash  
交互shell：输入命令bash启动  
bash start.sh 脚本解释器启动

![](pics9/shell7.jpg)
使用变量/环境变量需要加上$
![](pics9/shell8.jpg)
![](pics9/bash2.jpg)
-x 打印执行脚本时的内容轨迹
下面为启动一个新的bash进程，解释执行lsdir这个脚本文件，后面的都当作参数传递
![](pics9/bash3.jpg)
>在**当前**shell中执行脚本，会影响当前shell<br>
`. start.sh args`<br>
`source start.sh args`

## 命令历史
先前键入的命令都存于历史表
历史表存放于$HOME/.bash_history
表大小由HISTSIZE设定
![](pics9/env.jpg)
`history` 输出全部的命令历史
![](pics9/history.jpg)
![](pics9/export.jpg)
![](pics9/history2.jpg)

## alias
别名
![](pics9/alias.jpg)
![](pics9/alias2.jpg)
不写入初始化脚本中则下次启动shell就没有了

## tab补全
每行首个单词或管道命令后首个单词
TAB键搜索补全$PATH下的命令  
行中其他单词
搜索补全当前路径下的文件名
![](pics9/netstat.jpg)
alias n="" 定义别名n为后面整个命令，仅在当前终端有效  
cat -n显示行号  
awk 'NR>=30 && NR <41' 打印30-40行

## 输入重定向
sort < text.log sort 命令从文件获取输入
cat << word 从stdin获取数据直到再次遇到word（定界符） 
base64 <<< hello 将hello作为base64这个命令的输入

## 输出重定向与管道
![](pics9/std.jpg)
fd: file descriptor  
ls > ls.txt 相当于 ls 1>ls.txt 即将ls命令的输出stdout重定向到ls.txt文件，覆盖方式  
ls >> ls.txt 将ls命令的输出重定向到ls.txt文件，追加方式  
./main 2>error.log 将main程序的标准错误stdout(fd=2)重定向到error.log文件，覆盖方式  
2>&1 文件句柄2重定向到文件描述符1指向的文件  
除012外，其他文件句柄也可重定向
![](pics9/std2.jpg)
管道默认只传递stdout的内容，可用2>&1 |