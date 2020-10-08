#### 1.查看服务状态

ps es|grep ExporterStarter

#### 2.查看服务进程

jps
-q 只显示pid，不显示class名称,jar文件名和传递给main 方法的参数

$>  jps -q

28680

23789

23651

-m 输出传递给main 方法的参数，在嵌入式jvm上可能是null

$> jps -m

28715 Jps -m

23789 BossMain

23651 Resin -socketwait 32768 -stdout /data/aoxj/resin/log/stdout.log -stderr /data/aoxj/resin/log/stderr.log

-l 输出应用程序main class的完整package名 或者 应用程序的jar文件完整路径名

$> jps -l

28729 sun.tools.jps.Jps

23789 com.asiainfo.aimc.bossbi.BossMain

23651 com.caucho.server.resin.Resin

-v 输出传递给JVM的参数

$> jps -v

23789 BossMain

28802 Jps -Denv.class.path=/data/aoxj/bossbi/twsecurity/java/trustwork140.jar:/data/aoxj/bossbi/twsecurity/java/:/data/aoxj/bossbi/twsecurity/java/twcmcc.jar:/data/aoxj/jdk15/lib/rt.jar:/data/aoxj/jd

------------------------

ps -ef
ps -aux

#### 3.杀死进程

kill -9 pid    -9 表示强行终止进程

----------------------------------
https://blog.csdn.net/wfziyou/article/details/19169381

jps	基础工具
jstack	查看某个Java进程内的线程堆栈信息
jmap	jmap导出堆内存，然后使用jhat来进行分析
jhat	主要用来解析java堆dump并启动一个web服务器，然后就可以在浏览器中查看堆的dump文件
jstat	主要是对java应用程序的资源和性能进行实时的命令行监控，包括了对heap size和垃圾回收状况的监控
hprof	hprof能够展现CPU使用率，统计堆内存使用情况

-------------------top--------------------------

Tasks（系统任务）信息：total，总进程数；running，正在运行的进程数；sleeping，休眠的进程数；stopped，中止的进程数；zombie，僵死无响应的进程数。
CPU信息：us，用户占用；sy，内核占用；ni，优先级调度占用；id，空闲CPU；wa，I/O等待占用；hi，
硬件中断占用；si，软件中断占用；st，虚拟化占用。了解空闲的CPU百分比，主要看%id部分。
Mem（内存）信息：total，总内存空间；used，已用内存；free，空闲内存；buffers，缓存区域。
Swap（交换空间）信息：total，总交换空间；used，已用交换空间；free，空闲交换空间；cached，缓存空间。
在top命令的全屏操作界面中，按P键根据CPU占用情况对进程列表进行排序，或按M键根据内存占用情况排序，
按N键根据启动时间进行排序，按h键可以获得top程序的在线帮助信息，按q键可以正常地退出top程序。

若通过top排名工具发现某个进程CPU占用率非常高，需要终止该进程的运行时，
可以在top操作界面按k键，然后在列表上方将会出现“PID to kill”的提示信息，根据提示输入指定进程的PID号并按enter键确认即可终止对应的进程。

-----------------------------------------

#### 4.查找定位bug

cat */export-error | grep -10 ExportTask
cat export-info_20190918* | grep "ExcelUtilNew compress file result:{}"
cat export-info_201901012* | grep "not a standard excel file name"

  cat export-error_201901015* | grep "Assembly export data error:%s"
  cat */export-error | grep -10 Assembly export data error:%s

  部署在Linux下的程序，日志很多，而且实时滚动，可以通过以下方式快速查找自己自己想要的内容：

cat log.txt | grep 'ERROR' -A 5

意思是，在log.txt文件中，查找ERROR字符，并显示ERROR所在行的之后5行

cat log.txt | grep 'ERROR' -B?5? 之前5行

cat log.txt | grep 'ERROR' -C?5 前后5行

cat log.txt | grep -v 'ERROR' 排除ERROR所在的行


原文链接：https://blog.csdn.net/yuan882696yan/article/details/81663579


服务器 日志 cd /applogs/

 第一，tail -f run.log  ---------查看实时日志

              taif -5000 run.log  ------- 查看倒数5000行日志
    
          ctrl c    -----------退出
    
          -------------------------------------------
第二种，less 与 more 类似，但使用 less 可以随意浏览文件，而 more 仅能向前移动，却不能向后移动，而且 less 在查看之前不会加载整个文件。


              less run.log
            
              shift + G  -----------更新到最新日志
    
              shift + ?  + 关键字  ，向后搜索
    
          shift + /  + 关键字  ，向前搜索
    
          ----------------------------------------
    
              全屏导航
    
          ctrl + F ：向前移动一屏
    
              ctrl + B ：向后移动一屏
    
              ctrl + D ：向前移动半屏
    
              ctrl + U ：向后移动半屏
    
          单行导航
    
             j ： 向下移动一行
    
             k ： 向上移动一行

-------------------------------------------------------

G ： 移动到最后一行

g ： 移动到第一行

按空格：向下翻一页

b：向上翻一页

d：向下翻半页

u：向上翻半页

q / ZZ ： 退出 less 命令


	      /字符串：向下搜索"字符串"的功能
	          ?字符串：向上搜索"字符串"的功能
	          n：重复前一个搜索（与 / 或 ? 有关）
	          N：反向重复前一个搜索（与 / 或 ? 有关）
	          b 向后翻一页
	          d 向后翻半页
	          h 显示帮助界面
	          Q 退出less 命令
	          u 向前滚动半页
	          y 向前滚动一行
	          空格键 滚动一页
	          回车键 滚动一行
	          [pagedown]： 向下翻动一页
	          [pageup]： 向上翻动一页

第三，vim run.log   

              按 i 或者 o 进入插入状态
    
               ESC + ：q   ----------不保存离开
              
               ESC + ：q！   ----------不保存强制离开
    
               ESC + ：wq   ----------保存离开
    
               ESC + ：wq!   ----------强制保存离开
    
              ESC + : /findVideo   -------------查找findvideo关键字
    
              n ---------------向下查询
    
              N ---------------向上查询
              
              source /etc/profile：使参数生效；

3. 服务器重启命令

 重启命令放在 ：cd /opt



#### 5.查看服务是否挂了

ps -ef |grep com.yks.oms.ExporterStarter

jps -l

ps es|grep ExporterStarter

5. Ubuntu18.04查看本机IP

ifconfig

#### 6.下载Linux服务器文件到本地

Linux的sz和rz命令

 sudo apt-get install lrzsz

            sz filename   下载文件filename

　　　　　　sz file1 file2   下载多个文件

　　　　　　sz dir/*　　　下载dir目录下所有文件

#### 7.解压

解压缩
命令	描述
yum install zip unzip	安装zip、unzip应用
unzip Xxx.zip -d 解压到的目录	解压zip文件
tar -zxvf 文件名	解压tar.gz
tar参数

参数	意义
-z	通过gzip方式压缩或解压，最后以.tar.gz 为后缀
-x	解压，-C + 解压目录
-v	黑框框输出解压或压缩的过程
-f	后面+解压缩的文件名
-c	新建压缩文档
cxt(查看)(末尾加文件)u(更新压缩包中文件)这几个参数只能有一个参数

#### 8. 普通用户 "$",超级用户“#”

#### 9. 退出shell 

```
loginout
exit
Ctrl + D
```

#### 10. 删除光标位置前的单词

```
Ctrl + W
```

#### 11. 清空行

```
Ctrl + U
```

#### 12. 清空整个页面

```
clear
```

#### 13. 查看文件和目录

```
ls //
ls -F //递归查找
ls -ltr //按时间倒序排列
ls -a //显示隐藏文件

***********************
more 全部加载，只能向前不能向后
more -5 myLog.txt  // 每次展示5行，按空降进行下一页

******************************
less 不需要全部加载，向前或者向后
less -N myLog.txt // 显示行号
n // 下一个
N //上一个
/jinsheng  //
G // 最后一页
g //第一页
shift + G //实时刷新

less -N file1.txt file2.txt  //同时打开两个文件
：e // 输入文件名，进入该文件
：n //切换下一个文件
：p // 切换上一个文件




*******************************


```

#### 14. 查看CPU上下文切换

#####      14.1 安装sysstat

```
[root@iZ2zedlo8vsces82fnyzomZ ~]# yum  install  sysstat
```

#####     14.2  vmstat 1 5

```
[root@iZ2zedlo8vsces82fnyzomZ ~]# vmstat 1 5
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 205560  62632 1075528    0    0   182    20    1    1  2  1 97  0  0
 0  0      0 205560  62632 1075572    0    0     0     0 1604 2454  2  2 97  0  0
 0  0      0 205684  62632 1075572    0    0     0     0 1577 2587  2  1 97  0  0
 0  0      0 205684  62632 1075572    0    0     0    40 1536 2384  2  1 97  0  0
 0  0      0 205684  62632 1075572    0    0     0     0 1609 2450  2  1 97  0  0

// cs ,每秒上下文切换次数,值越大，sy（内核CPU）消耗的时间就越长
// us ,CPU用户进程使用时间,值越大，超过75%，就要考虑程序代码设计问题了
// sy ,CPU系统进程使用时间

```

#####      14.3 pidstat -w

```
　　11:25:36 PM   UID       PID   cswch/s nvcswch/s  Command
11:25:37 PM     0         1      1.00      0.00  systemd
11:25:37 PM     0         9    217.00      0.00  rcu_sched
11:25:37 PM     0        14      1.00      0.00  ksoftirqd/1
11:25:37 PM     0       318      1.00      0.00  kworker/1:1H
11:25:37 PM     0       325      3.00      0.00  kworker/0:1H
11:25:37 PM     0       330      3.00      0.00  jbd2/vda1-8
11:25:37 PM   999      3423     99.00      0.00  mongod
11:25:37 PM   999      4002      1.00      0.00  epmd
11:25:37 PM   999      7192     15.00      0.00  redis-server
11:25:37 PM   999      7248     16.00      0.00  redis-server
11:25:37 PM     0      9321      9.00      0.00  kworker/1:2
11:25:37 PM     0      9426      1.00      0.00  kworker/0:1
11:25:37 PM     0      9884     23.00      0.00  redis-sentinel
11:25:37 PM     0     10149     24.00      0.00  redis-sentinel
11:25:37 PM     0     10810      1.00      0.00  sshd
11:25:37 PM     0     11723      1.00      0.00  pidstat
11:25:37 PM     0     15838      1.00      0.00  apache2
11:25:37 PM     0     21540     23.00      0.00  redis-sentinel
11:25:37 PM     0     24254      1.00      0.00  AliYunDunUpdate
11:25:37 PM     0     24317     10.00      0.00  AliYunDun
11:25:37 PM   999     28332     17.00      0.00  redis-server
11:25:37 PM     0     29557     10.00      0.00  AliSecGuard
11:25:37 PM  1000     31483     10.00      0.00  node

　　
　　cswch/s（自愿）：值进程无法获取所需资源导致的上下文切换，比如：I/O，内存等系统资源不足时，就会发生自愿上下文切换

　　nvcswch/s（非自愿）：值进程由于时间已到等原因，被系统强制调度而发生的上下文切换，比如，大量进程都在争夺CPU而发生     非自愿上下文切换
　　
自愿的切换的多了，表明在等待资源，如IO
非自愿的切换的多了，表明CPU被任务竞争
中断数多，要结合/proc/interrupts分析具体中断情况

 
```

