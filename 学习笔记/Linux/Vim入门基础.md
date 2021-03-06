# Vim入门基础

```
$vim [filename]
打开文件,若不存在,就创建

vim [-version]

sudo apt remove vim-common

sudo apt install vim
```



### 1.常见规律

#### 大小写

``` 
通常,一对大小写字母提供相似的功能
小写命令在光标后面操作,大写命令在光标前面操作
```



#### 数字+命令

```
先数字n,后命令
一般表示执行n次命令
```



#### 命令组合

```
先执行前面的命令,后执行后面的命令
<start position> <command> <end position>
```



#### word与WORD

```
word的定义:
1.字母,数字,下划线的序列,用空白符分隔
2.其余非空白符的序列,用空白符分隔
3.空白+行

WORD的定义:
1.非空白符的序列,用空白符分隔
2.空白行
```



#### 模式

* `Normal`命令模式`Command mode`
  * 此模式下,字母会被识别为命令
  * `i`切换到插入模式
  * `:`切换到底线命令模式
* `Insert`插入模式`Insert mode`
  * `ESC`切换到命令模式
* 底线命令模式`Last line mode`
  * `ESC`退出底线命令模式

#### 帮助

```
:help <command>
```

### 2.命令模式

#### 移动

##### 单步

```
h	j	k	l
左  下   上  右
```

##### 单词

```
w	光标移动到下一个word的首部
e	光标移动到下一个word的末尾
b	光标移动到上一个word的首部
B	光标移动到上一个WORD的首部
```

##### 匹配

```
%
*
#
```

##### 本行

```
0 	到本行首部
^	到本行第一个非空字符
$ 	到本行末尾
g_	到本行最后一个非空字符
```

##### 多行

```
nG	到第n行
gg	到第一行
G	到最后一行
```

##### 翻页

```
ctrl+f		page down
ctrl+b		page up
```



#### 退出

```
ZZ 	大写的两个Z,保存并退出
```



#### 查找/替换

```/
/string		正向查找string字符串
?string		反向查找string字符串
n	下一个位置	
N	上一个位置

rc 用c替换当前字符
nrc	用c替换后面n个字符
```



#### 删除/复制/粘贴

```
删除
删除的同时,还会放入缓冲区等待粘贴
[n]x	在当前行,删除当前光标及之后的n个字符
dd 	删除当前行
ndd	删除n行

复制
yy	复制当前行到缓冲区

粘贴
p	小写,后向粘贴缓冲区内容
P	大写,前向粘贴内容
```



#### Undo/Redo/重复

```
u	undo撤销前一条命令,恢复原样
ctrl+r	redo

.	重复上一次修改正文的命令
n <command>	重复n次命令
```



### 3.插入模式



#### 进入插入模式

编辑模式下切换到插入模式

```
i	光标左侧
I	光标坐在行的开头
a	光标右侧(其实就是光标向右移动一位)
A	光标所在行的末尾
o	光标的下一行添加新行
O	光标的上一行添加新行
cw	替换光标后~word末尾
最后都会进入插入模式
```



#### 退出插入模式

退出插入模式,进入命令模式

```
ESC 或 ctrl+[
```



### 4.底线命令模式

#### 打开/保存/退出/切换

```
:e path/filename

:w
:w filename	另存为
:saveas	path/filename
:x	ZZ	:wq		保存并退出	:x表示仅在需要时保存

:q	未作修改时退出
:q!	放弃修改,直接退出	:qa!强行退出所有正在编辑的文件

:bn	切换到下一个文件
:bp	切换到上一个文件
:n	切换到下一个文件


```





#### 行号

```
:数字n	光标移到第n行
```



#### 查找

```
:/string/	正向查找
:?string?	反向查找
```



#### 正则表达式

```
^	行首
$	行尾
\<	字头
\>	子尾
\	转义
```



#### 删除

```
:d	删除当前行
```



#### 恢复文件

```
Vim在编辑文件时,会生成一个临时文件		以.开头,以.swp结尾
若Vim正常退出,则临时文件被删除
若意外退出,则可以用恢复命令来恢复文件	:recover
也可以在启动时用 -r选项
```



#### 选项设置

```
:set [option]	设置选项option
option包括:
autoindent	自动缩进
number		显示行号
```



#### Shell切换

```
:!shell_command		执行linux命令后回到vim
```



#### 分屏

```
:split(sp)		上下分屏
:vsplit(vsp)	v左右分屏

切换屏幕
ctrl+w+h	左屏
ctrl+w+j	下屏
ctrl+w+k	右屏
ctrl+w+l	上屏

w是window的缩写

ctrl+w+w	逆时针切换
```



### 5.小技巧

#### 行间移动

从短行到长行进行行切换的时候,会切换到短行的**最后一列**

从长到短行切换的话,列数不变





