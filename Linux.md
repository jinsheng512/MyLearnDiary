#### 1.�鿴����״̬

ps es|grep ExporterStarter

#### 2.�鿴�������

jps
-q ֻ��ʾpid������ʾclass����,jar�ļ����ʹ��ݸ�main �����Ĳ���

$>  jps -q

28680

23789

23651

-m ������ݸ�main �����Ĳ�������Ƕ��ʽjvm�Ͽ�����null

$> jps -m

28715 Jps -m

23789 BossMain

23651 Resin -socketwait 32768 -stdout /data/aoxj/resin/log/stdout.log -stderr /data/aoxj/resin/log/stderr.log

-l ���Ӧ�ó���main class������package�� ���� Ӧ�ó����jar�ļ�����·����

$> jps -l

28729 sun.tools.jps.Jps

23789 com.asiainfo.aimc.bossbi.BossMain

23651 com.caucho.server.resin.Resin

-v ������ݸ�JVM�Ĳ���

$> jps -v

23789 BossMain

28802 Jps -Denv.class.path=/data/aoxj/bossbi/twsecurity/java/trustwork140.jar:/data/aoxj/bossbi/twsecurity/java/:/data/aoxj/bossbi/twsecurity/java/twcmcc.jar:/data/aoxj/jdk15/lib/rt.jar:/data/aoxj/jd

------------------------

ps -ef
ps -aux

#### 3.ɱ������

kill -9 pid    -9 ��ʾǿ����ֹ����

----------------------------------
https://blog.csdn.net/wfziyou/article/details/19169381

jps	��������
jstack	�鿴ĳ��Java�����ڵ��̶߳�ջ��Ϣ
jmap	jmap�������ڴ棬Ȼ��ʹ��jhat�����з���
jhat	��Ҫ��������java��dump������һ��web��������Ȼ��Ϳ�����������в鿴�ѵ�dump�ļ�
jstat	��Ҫ�Ƕ�javaӦ�ó������Դ�����ܽ���ʵʱ�������м�أ������˶�heap size����������״���ļ��
hprof	hprof�ܹ�չ��CPUʹ���ʣ�ͳ�ƶ��ڴ�ʹ�����

-------------------top--------------------------

Tasks��ϵͳ������Ϣ��total���ܽ�������running���������еĽ�������sleeping�����ߵĽ�������stopped����ֹ�Ľ�������zombie����������Ӧ�Ľ�������
CPU��Ϣ��us���û�ռ�ã�sy���ں�ռ�ã�ni�����ȼ�����ռ�ã�id������CPU��wa��I/O�ȴ�ռ�ã�hi��
Ӳ���ж�ռ�ã�si������ж�ռ�ã�st�����⻯ռ�á��˽���е�CPU�ٷֱȣ���Ҫ��%id���֡�
Mem���ڴ棩��Ϣ��total�����ڴ�ռ䣻used�������ڴ棻free�������ڴ棻buffers����������
Swap�������ռ䣩��Ϣ��total���ܽ����ռ䣻used�����ý����ռ䣻free�����н����ռ䣻cached������ռ䡣
��top�����ȫ�����������У���P������CPUռ������Խ����б�������򣬻�M�������ڴ�ռ���������
��N����������ʱ��������򣬰�h�����Ի��top��������߰�����Ϣ����q�������������˳�top����

��ͨ��top�������߷���ĳ������CPUռ���ʷǳ��ߣ���Ҫ��ֹ�ý��̵�����ʱ��
������top�������水k����Ȼ�����б��Ϸ�������֡�PID to kill������ʾ��Ϣ��������ʾ����ָ�����̵�PID�Ų���enter��ȷ�ϼ�����ֹ��Ӧ�Ľ��̡�

-----------------------------------------

#### 4.���Ҷ�λbug

cat */export-error | grep -10 ExportTask
cat export-info_20190918* | grep "ExcelUtilNew compress file result:{}"
cat export-info_201901012* | grep "not a standard excel file name"

  cat export-error_201901015* | grep "Assembly export data error:%s"
  cat */export-error | grep -10 Assembly export data error:%s

  ������Linux�µĳ�����־�ܶ࣬����ʵʱ����������ͨ�����·�ʽ���ٲ����Լ��Լ���Ҫ�����ݣ�

cat log.txt | grep 'ERROR' -A 5

��˼�ǣ���log.txt�ļ��У�����ERROR�ַ�������ʾERROR�����е�֮��5��

cat log.txt | grep 'ERROR' -B?5? ֮ǰ5��

cat log.txt | grep 'ERROR' -C?5 ǰ��5��

cat log.txt | grep -v 'ERROR' �ų�ERROR���ڵ���


ԭ�����ӣ�https://blog.csdn.net/yuan882696yan/article/details/81663579


������ ��־ cd /applogs/

 ��һ��tail -f run.log  ---------�鿴ʵʱ��־

              taif -5000 run.log  ------- �鿴����5000����־
    
          ctrl c    -----------�˳�
    
          -------------------------------------------
�ڶ��֣�less �� more ���ƣ���ʹ�� less ������������ļ����� more ������ǰ�ƶ���ȴ��������ƶ������� less �ڲ鿴֮ǰ������������ļ���


              less run.log
            
              shift + G  -----------���µ�������־
    
              shift + ?  + �ؼ���  ���������
    
          shift + /  + �ؼ���  ����ǰ����
    
          ----------------------------------------
    
              ȫ������
    
          ctrl + F ����ǰ�ƶ�һ��
    
              ctrl + B ������ƶ�һ��
    
              ctrl + D ����ǰ�ƶ�����
    
              ctrl + U ������ƶ�����
    
          ���е���
    
             j �� �����ƶ�һ��
    
             k �� �����ƶ�һ��

-------------------------------------------------------

G �� �ƶ������һ��

g �� �ƶ�����һ��

���ո����·�һҳ

b�����Ϸ�һҳ

d�����·���ҳ

u�����Ϸ���ҳ

q / ZZ �� �˳� less ����


	      /�ַ�������������"�ַ���"�Ĺ���
	          ?�ַ�������������"�ַ���"�Ĺ���
	          n���ظ�ǰһ���������� / �� ? �йأ�
	          N�������ظ�ǰһ���������� / �� ? �йأ�
	          b ���һҳ
	          d ��󷭰�ҳ
	          h ��ʾ��������
	          Q �˳�less ����
	          u ��ǰ������ҳ
	          y ��ǰ����һ��
	          �ո�� ����һҳ
	          �س��� ����һ��
	          [pagedown]�� ���·���һҳ
	          [pageup]�� ���Ϸ���һҳ

������vim run.log   

              �� i ���� o �������״̬
    
               ESC + ��q   ----------�������뿪
              
               ESC + ��q��   ----------������ǿ���뿪
    
               ESC + ��wq   ----------�����뿪
    
               ESC + ��wq!   ----------ǿ�Ʊ����뿪
    
              ESC + : /findVideo   -------------����findvideo�ؼ���
    
              n ---------------���²�ѯ
    
              N ---------------���ϲ�ѯ
              
              source /etc/profile��ʹ������Ч��

3. ��������������

 ����������� ��cd /opt



#### 5.�鿴�����Ƿ����

ps -ef |grep com.yks.oms.ExporterStarter

jps -l

ps es|grep ExporterStarter

5. Ubuntu18.04�鿴����IP

ifconfig

#### 6.����Linux�������ļ�������

Linux��sz��rz����

 sudo apt-get install lrzsz

            sz filename   �����ļ�filename

������������sz file1 file2   ���ض���ļ�

������������sz dir/*����������dirĿ¼�������ļ�

#### 7.��ѹ

��ѹ��
����	����
yum install zip unzip	��װzip��unzipӦ��
unzip Xxx.zip -d ��ѹ����Ŀ¼	��ѹzip�ļ�
tar -zxvf �ļ���	��ѹtar.gz
tar����

����	����
-z	ͨ��gzip��ʽѹ�����ѹ�������.tar.gz Ϊ��׺
-x	��ѹ��-C + ��ѹĿ¼
-v	�ڿ�������ѹ��ѹ���Ĺ���
-f	����+��ѹ�����ļ���
-c	�½�ѹ���ĵ�
cxt(�鿴)(ĩβ���ļ�)u(����ѹ�������ļ�)�⼸������ֻ����һ������
