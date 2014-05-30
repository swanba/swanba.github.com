---
layout: post
title:  自定义saltstack modules
quote: 自定义saltstack modules
---

###自定义saltstack modules


1、先新建一个_module目录（file_root =/srv/salt）

    mkdir -p   /srv/salt/_modules
2、然后在_modules目录下 写个python脚本test.py 

    [root@node1 _modules]# cat test.py 
    #!/usr/bin/python
 
    # -*- coding: utf-8 -*-
 
    import os
    import datetime
 
    def run():
    return datetime.datetime.now().strftime( '%Y-%m-%d %H:%M:%S' )
3、写完模块后，同步到minion上

    [root@node1 _modules]#salt ‘*’ saltutil.sync_all
4、测试 （test为模块名字（即python脚本的名字）run为模块内的一个函数）

[root@node1 _modules]# salt '*'    test.run   测试环境有四台minion，返回结果如下     

    node2:
        2013-11-11 16:47:20
    node3:
        2013-11-11 16:47:22
    node4:
        2013-11-11 16:47:21
    node1:
        2013-11-11 16:47:27
 