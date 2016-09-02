# saltstack

�汾��1

Ŀ��:
    
    ��ȡ�����(minion)������ ������ʹ���ʡ��ڴ�ʹ�����������ʹ������������������� ��Ϣ

ʵ��˼·:
    
    1. �Զ���һ��salt modules �ű� ��hostinfo.py�� �ýű�������������(����Ҳ��ʹ��salt �Դ���moduels��functions����ȡ)
    2. ͬ��hostinfo.py��������ػ���minions��
    3. ��дpython�ű�(py_hostinfos.py)����salt api�ӿ� ʹ���Զ����hostinfo.py չʾ

ʵ������:

     1. ��װsaltstack �������:https://repo.saltstack.com/#rhel
     2. �����ڱ���ͬʱ��װ salt-master salt-minion(�������ʹ���������㼸�����㿴Ч��)
     3. ��master��minion�ֱ�����/etc/salt/master,/etc/salt/minion ʹ����master���� ʹ������ # salt "*" test.ping �ɹ�
     4. ��master���޸������ļ�/etc/salt/master
           file_roots:
	       base:
	           - /srv/salt
     5. �����Զ���ģ��Ŀ¼  #mkdir -p /srv/salt/_modules
       Ŀ¼�ṹ:
                [root@localhost ~]# cd /srv/
		[root@localhost srv]# tree
		.
		������ salt
		    ������ _modules
			������ hostinfo.py
     6. �� hostinfo.py ���뵽 _modules Ŀ¼��
     7. ͬ��������minion #salt '*' saltutil.sync_all
     8. ����py_hostinfos.py  (���չʾ�����Լ��޸�)����Ч������:
-------------------------------------------------------------------------------------------------------
[root@localhost python_shell]# ./py_hostinfos.py 
---------------------------hostname-----------------------------------
{'model.jsh315.com_tomcat3': {'id': 'model.jsh315.com_tomcat3'}, 'model.jsh315.com_tomcat2': {'id': 'model.jsh315.com_tomcat2'}, 'model.jsh315.com_tomcat1': {'id': 'model.jsh315.com_tomcat1'}, 'www.jsh315.com_salt_master': {'id': 'www.jsh315.com_salt_master'}, 'model.jsh315.com_nginx': {'id': 'model.jsh315.com_nginx'}}
---------------------------cpuinfo-----------------------------------
model.jsh315.com_tomcat3 cpu_usage:0
model.jsh315.com_tomcat2 cpu_usage:0
model.jsh315.com_tomcat1 cpu_usage:0
www.jsh315.com_salt_master cpu_usage:0
model.jsh315.com_nginx cpu_usage:0
---------------------------meminfo-------------------------------------
model.jsh315.com_tomcat3  MemTotal:990 Used:664  Free: 326 
model.jsh315.com_tomcat2  MemTotal:990 Used:665  Free: 325 
model.jsh315.com_tomcat1  MemTotal:990 Used:664  Free: 326 
www.jsh315.com_salt_master  MemTotal:990 Used:650  Free: 340 
model.jsh315.com_nginx  MemTotal:990 Used:667  Free: 323 
---------------------------networkinfo-------------------------------------
model.jsh315.com_tomcat3
lo in:0  out:0
eth0 in:353010  out:353010
--------------------------------
model.jsh315.com_tomcat2
lo in:0  out:0
eth0 in:354155  out:354155
--------------------------------
model.jsh315.com_tomcat1
lo in:0  out:0
eth0 in:354304  out:354304
--------------------------------
www.jsh315.com_salt_master
docker0 in:2970213  out:2970213
veth16d3852 in:573729  out:573729
lo in:1325337  out:1325337
veth1c76a4f in:1507553  out:1507553
veth31c0835 in:574715  out:574715
vethaa69ae6 in:573508  out:573508
eth0 in:18229480  out:18229480
--------------------------------
model.jsh315.com_nginx
lo in:0  out:0
eth0 in:512196  out:512196
--------------------------------
---------------------------diskinfo-------------------------------------
model.jsh315.com_tomcat3
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '9108228', '1K-blocks': '10190136', 'used': '541236', 'capacity': '6%', 'filesystem': '/dev/mapper/docker-8:17-262145-a759235479aae135337031d2cccfebb673d99e94b697180d9f4a08c7ab5f3dc5'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '65524', '1K-blocks': '65536', 'used': '12', 'capacity': '1%', 'filesystem': 'shm'}
model.jsh315.com_tomcat2
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '9108228', '1K-blocks': '10190136', 'used': '541236', 'capacity': '6%', 'filesystem': '/dev/mapper/docker-8:17-262145-ad58772de6214f16381c1ae179df1a8c184ec8245fd64725d93b23f4da588286'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '65524', '1K-blocks': '65536', 'used': '12', 'capacity': '1%', 'filesystem': 'shm'}
model.jsh315.com_tomcat1
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '9107932', '1K-blocks': '10190136', 'used': '541532', 'capacity': '6%', 'filesystem': '/dev/mapper/docker-8:17-262145-e72ae6736fa07e59271c360af287b4db35e35b8d9da523b9fc08a277ae2f6094'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '65524', '1K-blocks': '65536', 'used': '12', 'capacity': '1%', 'filesystem': 'shm'}
www.jsh315.com_salt_master
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '164328', '1K-blocks': '289293', 'used': '105509', 'capacity': '40%', 'filesystem': '/dev/sda1'}
{'available': '12827468', '1K-blocks': '18208184', 'used': '4432748', 'capacity': '26%', 'filesystem': '/dev/sda2'}
{'available': '506936', '1K-blocks': '507028', 'used': '92', 'capacity': '1%', 'filesystem': 'tmpfs'}
model.jsh315.com_nginx
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '9060360', '1K-blocks': '10190136', 'used': '589104', 'capacity': '7%', 'filesystem': '/dev/mapper/docker-8:17-262145-1503ca49817a6058d9ebe8f96e839187f9d76f2b854005a731c17005db713899'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '15899032', '1K-blocks': '20504628', 'used': '3540976', 'capacity': '19%', 'filesystem': '/dev/sdb1'}
{'available': '507028', '1K-blocks': '507028', 'used': '0', 'capacity': '0%', 'filesystem': 'tmpfs'}
{'available': '65524', '1K-blocks': '65536', 'used': '12', 'capacity': '1%', 'filesystem': 'shm'}

-------------------------------------------------------------------------------------------------------

python�汾2.4-2.7
Centos 6.5 64
Stackstack 2015-2016