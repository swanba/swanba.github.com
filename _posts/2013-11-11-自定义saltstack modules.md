---
layout: post
title:  �Զ���saltstack modules
quote: �Զ���saltstack modules
---

###�Զ���saltstack modules


1�����½�һ��_moduleĿ¼��file_root =/srv/salt��

    mkdir -p   /srv/salt/_modules
2��Ȼ����_modulesĿ¼�� д��python�ű�test.py 

    [root@node1 _modules]# cat test.py 
    #!/usr/bin/python
 
    # -*- coding: utf-8 -*-
 
    import os
    import datetime
 
    def run():
    return datetime.datetime.now().strftime( '%Y-%m-%d %H:%M:%S' )
3��д��ģ���ͬ����minion��

    [root@node1 _modules]#salt ��*�� saltutil.sync_all
4������ ��testΪģ�����֣���python�ű������֣�runΪģ���ڵ�һ��������

[root@node1 _modules]# salt '*'    test.run   ���Ի�������̨minion�����ؽ������     

    node2:
        2013-11-11 16:47:20
    node3:
        2013-11-11 16:47:22
    node4:
        2013-11-11 16:47:21
    node1:
        2013-11-11 16:47:27
 