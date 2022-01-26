## cmp
两文件逐字节比较
![](pics4/cmp.jpg)

## md5sum/sha1sum
文件内容比较
![](pics4/md5sum.jpg)
md5一般以16进制显示，共32个字符

## diff
求出两个文件的差别
![](pics4/diff.jpg)
git常用diff -u模式，改变处上下3行也会列出来。-u0模式没有上下文，即显示0行

## vi
文本编辑器
![](pics4/vi.jpg)
![](pics4/vi2.jpg)
也可在vi中输入:set ts=4设置tab为4字节  
vi有3种状态
![](pics4/vi3.jpg)
![](pics4/vi4.jpg)
>i当前字符前插入正文段，insert  
a当前字符后插入正文段，append  
hjkl同样相当于方向键控制光标移动
![](pics4/vi5.jpg)
方向键同理  
shift+PgUp/PgDn可上下翻页  
ctrl+f搜索  
^$快速移动到行首行尾  
wb分别表示左右移动一个单词，同样可以加数字  
:100移动到100行，其余同理, $表示最后一行
![](pics4/vi6.jpg)
x删除后面的一个字符  
dd删除一行  
u取消之前的编辑操作  
r替换光标指的字符  
.重复上次的操作  
ZZ存盘退出  
:wq回车 同上  
:w回车 存盘不退出  
:q!回车 不存盘退出  
![](pics4/vi7.jpg)
![](pics4/vi8.jpg)
co复制，m移动，d删除，y拷贝到剪切板  
J该行和下面一行两行合并   
ctrl+l刷新屏幕显示  
ctrl+g显示当前编辑信息  
![](pics4/vi9.jpg)
![](pics4/vi10.jpg)
不加g一行只替换一个，g表示全部替换  
REG中[]表示集合，匹配其内任意一个字符，a*表示匹配0或任意个a字符，加\转义才可
![](pics4/vi11.jpg)

## vi死机
不能按ctrl+s，linux会进入流量控制状态，好像死机，ctrl+q解除
![](pics4/vi12.jpg)
![](pics4/vi13.jpg)

## 意外终止问题
存盘时程序意外中止，文件内容不变  
shift+z按两次存盘退出按成ctrl+z，导致进程被挂起（suspend），暂停运行（处于stopped状态）
![](pics4/vi14.jpg)

## 退格键无法使用
程序运行，处于输入状态时退格键无法正常使用，原因：行律设置不正确
![](pics4/vi15.jpg)
![](pics4/stty.jpg)

## 显示乱码
![](pics4/error1.jpg)
linux默认使用7比特ASCII字符集

## 文本文件格式问题
![](pics4/error2.jpg)
![](pics4/error3.jpg)
![](pics4/od.jpg)
dos2unix/unix2dos todos/frodos都可进行转换  
file 查看文件类型

## 中文编码问题
![](pics4/error4.jpg)
env | grep LANG 查看与语言有关环境变量
![](pics4/od2.jpg)
共六个字节，0a为换行符
![](pics4/iconv.jpg)
![](pics4/iconv2.jpg)