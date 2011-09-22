---
layout: post
title: Linux Process States, processes which stuck into state D
---

Here are the different values that the s, stat and state output specifiers
(header "STAT" or "S") will display to describe the state of a process.

- D Uninterruptible sleep (usually IO)
- R Running or runnable (on run queue)
- S Interruptible sleep (waiting for an event to complete)
- T Stopped, either by a job control signal or because it is being traced.
- W paging (not valid since the 2.6.xx kernel)
- X dead (should never be seen)
- Z Defunct ("zombie") process, terminated but not reaped by its parent.

For BSD formats and when the stat keyword is used, additional characters may be displayed:

- < high-priority (not nice to other users)
- N low-priority (nice to other users)
- L has pages locked into memory (for real-time and custom IO)
- s is a session leader
- l is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
- + is in the foreground process group


sudo ps axjfww

    app@ip-10-50-41-169:~$ sudo ps axjfww
     PPID   PID  PGID   SID TTY      TPGID STAT   UID   TIME COMMAND
        0     2     0     0 ?           -1 S        0   0:00 [kthreadd]
        2     3     0     0 ?           -1 S        0   1:14  \_ [ksoftirqd/0]
        2     4     0     0 ?           -1 S        0   0:15  \_ [migration/0]
        2     5     0     0 ?           -1 S        0   0:00  \_ [watchdog/0]
        2     6     0     0 ?           -1 S        0   0:07  \_ [migration/1]
        2     7     0     0 ?           -1 S        0   0:35  \_ [ksoftirqd/1]
        2     8     0     0 ?           -1 S        0   0:00  \_ [watchdog/1]
        2     9     0     0 ?           -1 S        0   1:18  \_ [events/0]
        2    10     0     0 ?           -1 S        0   0:33  \_ [events/1]
        2    11     0     0 ?           -1 S        0   0:00  \_ [cpuset]
        2    12     0     0 ?           -1 S        0   0:00  \_ [khelper]
        2    13     0     0 ?           -1 S        0   0:00  \_ [netns]
        2    14     0     0 ?           -1 S        0   0:00  \_ [async/mgr]
        2    15     0     0 ?           -1 S        0   0:00  \_ [pm]
        2    17     0     0 ?           -1 S        0   0:00  \_ [xenwatch]
        2    18     0     0 ?           -1 S        0   0:00  \_ [xenbus]
        2    19     0     0 ?           -1 S        0   0:03  \_ [sync_supers]
        2    20     0     0 ?           -1 S        0   0:05  \_ [bdi-default]
        2    21     0     0 ?           -1 S        0   0:00  \_ [kintegrityd/0]
        2    22     0     0 ?           -1 S        0   0:00  \_ [kintegrityd/1]
        2    23     0     0 ?           -1 S        0   0:02  \_ [kblockd/0]
        2    24     0     0 ?           -1 S        0   0:00  \_ [kblockd/1]
        2    25     0     0 ?           -1 S        0   0:00  \_ [ata_aux]
        2    26     0     0 ?           -1 S        0   0:00  \_ [ata_sff/0]
        2    27     0     0 ?           -1 S        0   0:00  \_ [ata_sff/1]
        2    28     0     0 ?           -1 S        0   0:00  \_ [khubd]
        2    29     0     0 ?           -1 S        0   0:00  \_ [kseriod]
        2    30     0     0 ?           -1 S        0   0:00  \_ [kmmcd]
        2    31     0     0 ?           -1 S        0   0:00  \_ [khungtaskd]
        2    32     0     0 ?           -1 S        0   0:57  \_ [kswapd0]
        2    33     0     0 ?           -1 SN       0   0:00  \_ [ksmd]
        2    34     0     0 ?           -1 S        0   0:00  \_ [aio/0]
        2    35     0     0 ?           -1 S        0   0:00  \_ [aio/1]
        2    36     0     0 ?           -1 S        0   0:00  \_ [ecryptfs-kthrea]
        2    37     0     0 ?           -1 S        0   0:00  \_ [crypto/0]
        2    38     0     0 ?           -1 S        0   0:00  \_ [crypto/1]
        2    43     0     0 ?           -1 S        0   0:00  \_ [khvcd]
        2    44     0     0 ?           -1 S        0   0:00  \_ [kstriped]
        2    45     0     0 ?           -1 S        0   0:00  \_ [kmpathd/0]
        2    46     0     0 ?           -1 S        0   0:00  \_ [kmpathd/1]
        2    47     0     0 ?           -1 S        0   0:00  \_ [kmpath_handlerd]
        2    48     0     0 ?           -1 S        0   0:00  \_ [ksnapd]
        2    49     0     0 ?           -1 S        0   0:00  \_ [kondemand/0]
        2    50     0     0 ?           -1 S        0   0:00  \_ [kondemand/1]
        2    51     0     0 ?           -1 S        0   0:00  \_ [kconservative/0]
        2    52     0     0 ?           -1 S        0   0:00  \_ [kconservative/1]
        2   184     0     0 ?           -1 S        0   0:24  \_ [jbd2/sda1-8]
        2   185     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
        2   186     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
        2   594     0     0 ?           -1 S        0   0:00  \_ [kjournald]
        2 22189     0     0 ?           -1 S        0   0:08  \_ [flush-202:1]
        2 28093     0     0 ?           -1 S        0   0:54  \_ [jbd2/sdj-8]
        2 28094     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
        2 28095     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
        2  7778     0     0 ?           -1 S        0   1:23  \_ [flush-202:144]
        0     1     1     1 ?           -1 Ss       0   0:05 /sbin/init
        1   229   227   227 ?           -1 S        0   0:00 upstart-udev-bridge --daemon
        1   233   233   233 ?           -1 S<s      0   0:00 udevd --daemon
      233   298   233   233 ?           -1 S<       0   0:00  \_ udevd --daemon
      233   324   233   233 ?           -1 S<       0   0:00  \_ udevd --daemon
        1   422   422   422 ?           -1 Ss       0   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
        1   569   546   546 ?           -1 Sl     101   0:18 rsyslogd -c4
        1   581   581   581 ?           -1 Ss     102   0:01 dbus-daemon --system --fork
        1   606   606   606 tty4       606 Ss+      0   0:00 /sbin/getty -8 38400 tty4
        1   611   611   611 tty5       611 Ss+      0   0:00 /sbin/getty -8 38400 tty5
        1   615   615   615 tty2       615 Ss+      0   0:00 /sbin/getty -8 38400 tty2
        1   616   616   616 tty3       616 Ss+      0   0:00 /sbin/getty -8 38400 tty3
        1   618   618   618 tty6       618 Ss+      0   0:00 /sbin/getty -8 38400 tty6
        1   620   620   620 ?           -1 Ss       1   0:00 atd
        1   626   626   626 ?           -1 Ss       0   3:20 /usr/sbin/irqbalance
        1   671   671   671 tty1       671 Ss+      0   0:00 /sbin/getty -8 38400 tty1
        1   687   581   581 ?           -1 Sl       0   0:20 /usr/sbin/console-kit-daemon --no-daemon
        1 30111 30111 30111 ?           -1 Ss       0   1:55 /usr/sbin/munin-node
        1  1114  1114  1114 ?           -1 Ss       1   0:00 portmap
        1  1330  1330  1330 ?           -1 Ss     110   0:00 rpc.statd -L
        1 15775 15775 15775 ?           -1 Ssl   1001   2:37 memcached -d
        1 10976 10976 10655 ?           -1 R     1001 9443:14 /usr/local/bin/ruby script/rails c
        1 23523 23523 23523 ?           -1 Ssl      0   1:22 /usr/sbin/glusterfsd --xlator-option glustervolume-server.listen-port=24009 -s localhost --volfile-id glustervolume.asics2-production-draft.home-app-glustervolume -p /etc/glusterd/vols/glustervolume/run/asics2-production-draft-home-app-glustervolume.pid -S /tmp/066493995b368291ee8fb11715a0af5e.socket --brick-name /home/app/glustervolume --brick-port 24009 -l /var/log/glusterfs/bricks/home-app-glustervolume.log
        1 23930 23930 23930 ?           -1 Ssl      0   1:10 /usr/sbin/glusterfs --log-level=INFO --volfile-id=glustervolume --volfile-server=asics2-production-draft /home/app/gluster
        1 25031 25031 25031 ?           -1 Ss       0   0:03 /usr/sbin/sshd
    25031 20996 20996 20996 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    20996 21020 20996 20996 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/1  
    21020 21021 21021 21021 pts/1    21021 Ss+   1001   0:00  |       \_ -bash
    25031 21171 21171 21171 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    21171 21196 21171 21171 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/0  
    21196 21197 21197 21197 pts/0    25722 Ss    1001   0:00  |       \_ -bash
    21197 25541 25541 21197 pts/0    25722 T     1001   0:00  |           \_ vim app/models/newsletter.rb
    21197 25722 25722 21197 pts/0    25722 Sl+   1001   0:49  |           \_ /usr/local/bin/ruby script/rails c production_draft
    25031 22956 22956 22956 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    22956 22980 22956 22956 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/2  
    22980 22981 22981 22981 pts/2    22981 Ss+   1001   0:00  |       \_ -bash
    25031 26061 26061 26061 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    26061 26085 26061 26061 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/4  
    26085 26086 26086 26086 pts/4    27671 Ss    1001   0:01  |       \_ -bash
    26086 27671 27671 26086 pts/4    27671 R+       0   0:00  |           \_ ps axjfww
    25031 26129 26129 26129 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    26129 26154 26129 26129 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/5  
    26154 26155 26155 26155 pts/5    26386 Ss    1001   0:00  |       \_ -bash
    26155 26386 26386 26155 pts/5    26386 S+       0   0:00  |           \_ /bin/bash
    25031 26292 26292 26292 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    26292 26316 26292 26292 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/6  
    26316 26317 26317 26317 pts/6    26382 Ss    1001   0:00  |       \_ -bash
    26317 26382 26382 26317 pts/6    26382 S+    1001   0:00  |           \_ tail -f unicorn.err.log
    25031 26599 26599 26599 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    26599 26623 26599 26599 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/8  
    26623 26624 26624 26624 pts/8    26624 Ss+   1001   0:01  |       \_ -bash
    25031 26917 26917 26917 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
    26917 26942 26917 26917 ?           -1 S     1001   0:00      \_ sshd: app@pts/9  
    26942 26943 26943 26943 pts/9    26943 Ss+   1001   0:00          \_ -bash
        1  2696  2696  2696 ?           -1 Ss       0   0:00 nginx: master process /usr/sbin/nginx
     2696  3490  2696  2696 ?           -1 S       33   0:02  \_ nginx: worker process
     2696  3491  2696  2696 ?           -1 S       33   0:03  \_ nginx: worker process
     2696  3492  2696  2696 ?           -1 S       33   0:03  \_ nginx: worker process
     2696  3493  2696  2696 ?           -1 S       33   0:02  \_ nginx: worker process
        1 16747 16747 16747 ?           -1 Ss       0   0:00 cron
        1 30265 30265 30265 ?           -1 Ss       0   0:00 /usr/lib/postfix/master
    30265 30267 30265 30265 ?           -1 S      106   0:00  \_ qmgr -l -t fifo -u
    30265  5728 30265 30265 ?           -1 S      106   0:00  \_ tlsmgr -l -t unix -u
    30265 25822 30265 30265 ?           -1 S      106   0:00  \_ pickup -l -t fifo -u
        1 30686 30686 30686 ?           -1 Ssl      0   0:06 /usr/sbin/glusterd -p /var/run/glusterd.pid
        1 30750 30750 30750 ?           -1 Ssl      0   0:01 /usr/sbin/glusterfs -f /etc/glusterd/nfs/nfs-server.vol -p /etc/glusterd/nfs/run/nfs.pid -l /var/log/glusterfs/nfs.log
        1  8604  8587  8587 ?           -1 D     1001   2:58 unicorn worker[0] -E production_draft -D -c /home/app/app_draft/current/config/system/unicorn.conf.rb                                          
        1  8607  8587  8587 ?           -1 D     1001   2:50 unicorn worker[1] -E production_draft -D -c /home/app/app_draft/current/config/system/unicorn.conf.rb                                          
     8607 10059  8587  8587 ?           -1 Z     1001   0:00  \_ [sh] <defunct>
        1 10064  8587  8587 ?           -1 D     1001   1:07 ruby /home/app/bundle/ruby/1.9.1/bin/rake qor:job:run JOB=import_stores WORKER_ID=85 RAILS_ENV=production_draft NO_I18N_CACHE=1 --trace




lsof|grep 10064
        app@ip-10-50-41-169:~$ lsof|grep 10064
        ruby      10064        app  cwd       DIR            202,144     4096 24649082 /home/app/app_draft/releases/20110915124241
        ruby      10064        app  rtd       DIR              202,1     4096        2 /
        ruby      10064        app  txt       REG              202,1  7027839   134325 /usr/local/bin/ruby
        ruby      10064        app  mem       REG              202,1   122877   275680 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/trans/single_byte.so
        ruby      10064        app  mem       REG              202,1    51712   148843 /lib/libnss_files-2.12.1.so
        ruby      10064        app  mem       REG              202,1    88384   131392 /lib/libgcc_s.so.1
        ruby      10064        app  mem       REG              202,1   348234   275709 /usr/local/lib/ruby/1.9.1/x86_64-linux/syck.so
        ruby      10064        app  mem       REG              202,1    24192   275701 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/shift_jis.so
        ruby      10064        app  mem       REG              202,1    24544   275661 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/euc_jp.so
        ruby      10064        app  mem       REG              202,1   419107   275724 /usr/local/lib/ruby/1.9.1/x86_64-linux/nkf.so
        ruby      10064        app  mem       REG              202,1    67084   275731 /usr/local/lib/ruby/1.9.1/x86_64-linux/iconv.so
        ruby      10064        app  mem       REG            202,144   169052  8783942 /home/app/bundle/ruby/1.9.1/gems/yajl-ruby-0.8.3/ext/yajl/yajl.so
        ruby      10064        app  mem       REG            202,144    19819  8783243 /home/app/bundle/ruby/1.9.1/gems/hpricot-0.8.4/lib/fast_xs.so
        ruby      10064        app  mem       REG            202,144   281015  8783249 /home/app/bundle/ruby/1.9.1/gems/hpricot-0.8.4/lib/hpricot_scan.so
        ruby      10064        app  mem       REG              202,1    47204   275729 /usr/local/lib/ruby/1.9.1/x86_64-linux/racc/cparse.so
        ruby      10064        app  mem       REG              202,1    14344   131395 /lib/libgpg-error.so.0.4.0
        ruby      10064        app  mem       REG              202,1   490936   131393 /lib/libgcrypt.so.11.5.3
        ruby      10064        app  mem       REG              202,1  1364056   162533 /usr/lib/libxml2.so.2.7.7
        ruby      10064        app  mem       REG              202,1   237416   143639 /usr/lib/libxslt.so.1.1.26
        ruby      10064        app  mem       REG              202,1    80832   142407 /usr/lib/libexslt.so.0.8.15
        ruby      10064        app  mem       REG            202,144   454463  8651883 /home/app/bundle/ruby/1.9.1/gems/nokogiri-1.5.0/lib/nokogiri/nokogiri.so
        ruby      10064        app  mem       REG              202,1    13130   275733 /usr/local/lib/ruby/1.9.1/x86_64-linux/digest/md5.so
        ruby      10064        app  mem       REG            202,144   134033 10620377 /home/app/bundle/ruby/1.9.1/gems/json-1.6.0/ext/json/ext/json/ext/generator.so
        ruby      10064        app  mem       REG              202,1    13580   275698 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/utf_32le.so
        ruby      10064        app  mem       REG              202,1    13596   275706 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/utf_32be.so
        ruby      10064        app  mem       REG              202,1    15164   275691 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/utf_16le.so
        ruby      10064        app  mem       REG              202,1    15156   275689 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/utf_16be.so
        ruby      10064        app  mem       REG            202,144    60927 10620372 /home/app/bundle/ruby/1.9.1/gems/json-1.6.0/ext/json/ext/json/ext/parser.so
        ruby      10064        app  mem       REG            202,144    69578 10619932 /home/app/bundle/ruby/1.9.1/gems/bcrypt-ruby-3.0.1/lib/bcrypt_ext.so
        ruby      10064        app  mem       REG              202,1    97256   148500 /lib/libnsl-2.12.1.so
        ruby      10064        app  mem       REG              202,1  2156448   158891 /usr/lib/libmysqlclient_r.so.16.0.0
        ruby      10064        app  mem       REG            202,144   102248  8916322 /home/app/bundle/ruby/1.9.1/gems/mysql2-0.3.7/lib/mysql2/mysql2.so
        ruby      10064        app  mem       REG            202,144    88464  8784271 /home/app/bundle/ruby/1.9.1/gems/raindrops-0.7.0/lib/raindrops_ext.so
        ruby      10064        app  mem       REG            202,144   125001  8917127 /home/app/bundle/ruby/1.9.1/gems/unicorn-4.1.1/lib/unicorn_http.so
        ruby      10064        app  mem       REG            202,144   132666  8783579 /home/app/bundle/ruby/1.9.1/gems/kgio-2.6.0/lib/kgio_ext.so
        ruby      10064        app  mem       REG              202,1   432923   275726 /usr/local/lib/ruby/1.9.1/x86_64-linux/socket.so
        ruby      10064        app  mem       REG              202,1   182066   275710 /usr/local/lib/ruby/1.9.1/x86_64-linux/bigdecimal.so
        ruby      10064        app  mem       REG              202,1    11017   275738 /usr/local/lib/ruby/1.9.1/x86_64-linux/fcntl.so
        ruby      10064        app  mem       REG              202,1   333904   134429 /lib/libssl.so.0.9.8
        ruby      10064        app  mem       REG              202,1  1064196   275712 /usr/local/lib/ruby/1.9.1/x86_64-linux/openssl.so
        ruby      10064        app  mem       REG              202,1   168849   275725 /usr/local/lib/ruby/1.9.1/x86_64-linux/zlib.so
        ruby      10064        app  mem       REG              202,1    17252   275684 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/iso_8859_1.so
        ruby      10064        app  mem       REG              202,1    45944   275653 /usr/local/lib/ruby/1.9.1/x86_64-linux/digest.so
        ruby      10064        app  mem       REG              202,1    96816   131448 /lib/libz.so.1.2.3.4
        ruby      10064        app  mem       REG              202,1  1608192   134428 /lib/libcrypto.so.0.9.8
        ruby      10064        app  mem       REG              202,1    14122   275737 /usr/local/lib/ruby/1.9.1/x86_64-linux/digest/sha1.so
        ruby      10064        app  mem       REG              202,1    59793   275740 /usr/local/lib/ruby/1.9.1/x86_64-linux/strscan.so
        ruby      10064        app  mem       REG              202,1    83297   275652 /usr/local/lib/ruby/1.9.1/x86_64-linux/stringio.so
        ruby      10064        app  mem       REG              202,1   326788   154374 /usr/local/lib/libyaml-0.so.2.0.2
        ruby      10064        app  mem       REG              202,1    73599   275711 /usr/local/lib/ruby/1.9.1/x86_64-linux/psych.so
        ruby      10064        app  mem       REG              202,1    32604   275749 /usr/local/lib/ruby/1.9.1/x86_64-linux/etc.so
        ruby      10064        app  mem       REG              202,1    13482   275672 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/trans/transdb.so
        ruby      10064        app  mem       REG              202,1    13562   275702 /usr/local/lib/ruby/1.9.1/x86_64-linux/enc/encdb.so
        ruby      10064        app  mem       REG              202,1    26048   158202 /usr/lib/gconv/gconv-modules.cache
        ruby      10064        app  mem       REG              202,1  1572232   143041 /lib/libc-2.12.1.so
        ruby      10064        app  mem       REG              202,1   534832   147913 /lib/libm-2.12.1.so
        ruby      10064        app  mem       REG              202,1    43296   146182 /lib/libcrypt-2.12.1.so
        ruby      10064        app  mem       REG              202,1    14696   148883 /lib/libdl-2.12.1.so
        ruby      10064        app  mem       REG              202,1    31744   140621 /lib/librt-2.12.1.so
        ruby      10064        app  mem       REG              202,1   136067   143043 /lib/libpthread-2.12.1.so
        ruby      10064        app  mem       REG              202,1   141072   147938 /lib/ld-2.12.1.so
        ruby      10064        app  mem       REG              202,1  1779392   131410 /usr/lib/locale/locale-archive
        ruby      10064        app    0r      CHR                1,3      0t0     4266 /dev/null
        ruby      10064        app    1w      REG            202,144    18999 24649137 /home/app/app_draft/shared/log/unicorn.out.log
        ruby      10064        app    2w      REG            202,144  7442088 24649136 /home/app/app_draft/shared/log/unicorn.err.log
        ruby      10064        app    3r      CHR                1,3      0t0     4266 /dev/null
        ruby      10064        app    4w      CHR                1,3      0t0     4266 /dev/null
        ruby      10064        app    5r      CHR                1,3      0t0     4266 /dev/null
        ruby      10064        app    6w      CHR                1,3      0t0     4266 /dev/null
        ruby      10064        app    7w      REG            202,144 58185087 24649133 /home/app/app_draft/shared/log/production_draft.log
        ruby      10064        app    8u     IPv4            7244229      0t0      TCP mysqldevhost:60003->masterhost:mysql (CLOSE_WAIT)
        ruby      10064        app    9w      REG            202,144 58185087 24649133 /home/app/app_draft/shared/log/production_draft.log
        ruby      10064        app   10u     IPv4            7230458      0t0      TCP mysqldevhost:40718->memcachedhost:11211 (ESTABLISHED)
        ruby      10064        app   11u     IPv4            7230459      0t0      TCP mysqldevhost:40566->masterhost:mysql (CLOSE_WAIT)
        ruby      10064        app   12u      REG              202,1   104351   279265 /tmp/RackMultipart20110915-8607-14xzzyi (deleted)
        ruby      10064        app   13u      REG              202,1   444091   279288 /tmp/RackMultipart20110915-8607-14ekd0t
        ruby      10064        app   14u      REG              202,1   104347   279289 /tmp/RackMultipart20110915-8607-sk1xi
        ruby      10064        app   15u     IPv4            7244233      0t0      TCP mysqldevhost:51678->memcachedhost:11211 (ESTABLISHED)




        app@ip-10-50-41-169:~$ sudo ps axjfww
         PPID   PID  PGID   SID TTY      TPGID STAT   UID   TIME COMMAND
            0     2     0     0 ?           -1 S        0   0:00 [kthreadd]
            2     3     0     0 ?           -1 S        0   0:00  \_ [ksoftirqd/0]
            2     4     0     0 ?           -1 S        0   0:00  \_ [migration/0]
            2     5     0     0 ?           -1 S        0   0:00  \_ [watchdog/0]
            2     6     0     0 ?           -1 S        0   0:00  \_ [migration/1]
            2     7     0     0 ?           -1 S        0   0:00  \_ [ksoftirqd/1]
            2     8     0     0 ?           -1 S        0   0:00  \_ [watchdog/1]
            2     9     0     0 ?           -1 S        0   0:00  \_ [events/0]
            2    10     0     0 ?           -1 S        0   0:00  \_ [events/1]
            2    11     0     0 ?           -1 S        0   0:00  \_ [cpuset]
            2    12     0     0 ?           -1 S        0   0:00  \_ [khelper]
            2    13     0     0 ?           -1 S        0   0:00  \_ [netns]
            2    14     0     0 ?           -1 S        0   0:00  \_ [async/mgr]
            2    15     0     0 ?           -1 S        0   0:00  \_ [pm]
            2    17     0     0 ?           -1 S        0   0:00  \_ [xenwatch]
            2    18     0     0 ?           -1 S        0   0:00  \_ [xenbus]
            2    19     0     0 ?           -1 S        0   0:00  \_ [sync_supers]
            2    20     0     0 ?           -1 S        0   0:00  \_ [bdi-default]
            2    21     0     0 ?           -1 S        0   0:00  \_ [kintegrityd/0]
            2    22     0     0 ?           -1 S        0   0:00  \_ [kintegrityd/1]
            2    23     0     0 ?           -1 S        0   0:00  \_ [kblockd/0]
            2    24     0     0 ?           -1 S        0   0:00  \_ [kblockd/1]
            2    25     0     0 ?           -1 S        0   0:00  \_ [ata_aux]
            2    26     0     0 ?           -1 S        0   0:00  \_ [ata_sff/0]
            2    27     0     0 ?           -1 S        0   0:00  \_ [ata_sff/1]
            2    28     0     0 ?           -1 S        0   0:00  \_ [khubd]
            2    29     0     0 ?           -1 S        0   0:00  \_ [kseriod]
            2    30     0     0 ?           -1 S        0   0:00  \_ [kmmcd]
            2    31     0     0 ?           -1 S        0   0:00  \_ [khungtaskd]
            2    32     0     0 ?           -1 S        0   0:00  \_ [kswapd0]
            2    33     0     0 ?           -1 SN       0   0:00  \_ [ksmd]
            2    34     0     0 ?           -1 S        0   0:00  \_ [aio/0]
            2    35     0     0 ?           -1 S        0   0:00  \_ [aio/1]
            2    36     0     0 ?           -1 S        0   0:00  \_ [ecryptfs-kthrea]
            2    37     0     0 ?           -1 S        0   0:00  \_ [crypto/0]
            2    38     0     0 ?           -1 S        0   0:00  \_ [crypto/1]
            2    43     0     0 ?           -1 S        0   0:00  \_ [khvcd]
            2    44     0     0 ?           -1 S        0   0:00  \_ [kstriped]
            2    45     0     0 ?           -1 S        0   0:00  \_ [kmpathd/0]
            2    46     0     0 ?           -1 S        0   0:00  \_ [kmpathd/1]
            2    47     0     0 ?           -1 S        0   0:00  \_ [kmpath_handlerd]
            2    48     0     0 ?           -1 S        0   0:00  \_ [ksnapd]
            2    49     0     0 ?           -1 S        0   0:00  \_ [kondemand/0]
            2    50     0     0 ?           -1 S        0   0:00  \_ [kondemand/1]
            2    51     0     0 ?           -1 S        0   0:00  \_ [kconservative/0]
            2    52     0     0 ?           -1 S        0   0:00  \_ [kconservative/1]
            2   190     0     0 ?           -1 S        0   0:00  \_ [jbd2/sda1-8]
            2   191     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
            2   192     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
            2   501     0     0 ?           -1 S        0   0:00  \_ [flush-202:1]
            2   503     0     0 ?           -1 S        0   0:00  \_ [flush-202:144]
            2   520     0     0 ?           -1 S        0   0:00  \_ [jbd2/sdj-8]
            2   521     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
            2   522     0     0 ?           -1 S        0   0:00  \_ [ext4-dio-unwrit]
            2   585     0     0 ?           -1 S        0   0:00  \_ [kjournald]
            0     1     1     1 ?           -1 Ss       0   0:00 /sbin/init
            1   229   228   228 ?           -1 S        0   0:00 upstart-udev-bridge --daemon
            1   238   238   238 ?           -1 S<s      0   0:00 udevd --daemon
          238   290   238   238 ?           -1 S<       0   0:00  \_ udevd --daemon
          238   291   238   238 ?           -1 S<       0   0:00  \_ udevd --daemon
            1   403   403   403 ?           -1 Ss       1   0:00 portmap
            1   448   448   448 ?           -1 Ss       0   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
            1   592   548   548 ?           -1 Sl     101   0:00 rsyslogd -c4
            1   597   597   597 ?           -1 Ss     110   0:00 rpc.statd -L
            1   618   618   618 ?           -1 Ss       0   0:00 /usr/sbin/sshd
          618  1135  1135  1135 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
         1135  1227  1135  1135 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/0  
         1227  1228  1228  1228 pts/0     1228 Ss+   1001   0:00  |       \_ -bash
          618  1266  1266  1266 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
         1266  1290  1266  1266 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/1  
         1290  1291  1291  1291 pts/1     1946 Ss    1001   0:00  |       \_ -bash
         1291  1946  1946  1291 pts/1     1946 R+       0   0:00  |           \_ ps axjfww
          618  1632  1632  1632 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
         1632  1660  1632  1632 ?           -1 S     1001   0:00  |   \_ sshd: app@pts/2  
         1660  1661  1661  1661 pts/2     1708 Ss    1001   0:00  |       \_ -bash
         1661  1708  1708  1661 pts/2     1708 Sl+   1001   0:41  |           \_ /usr/local/bin/ruby script/rails c
          618  1782  1782  1782 ?           -1 Ss       0   0:00  \_ sshd: app [priv] 
         1782  1810  1782  1782 ?           -1 S     1001   0:00      \_ sshd: app@pts/3  
         1810  1811  1811  1811 pts/3     1890 Ss    1001   0:00          \_ -bash
         1811  1890  1890  1811 pts/3     1890 S+    1001   0:00              \_ tail -f log/production_draft.log
            1   619   619   619 ?           -1 Ss     102   0:00 dbus-daemon --system --fork
            1   622   622   622 tty4       622 Ss+      0   0:00 /sbin/getty -8 38400 tty4
            1   625   625   625 tty5       625 Ss+      0   0:00 /sbin/getty -8 38400 tty5
            1   630   630   630 tty2       630 Ss+      0   0:00 /sbin/getty -8 38400 tty2
            1   631   631   631 tty3       631 Ss+      0   0:00 /sbin/getty -8 38400 tty3
            1   634   634   634 tty6       634 Ss+      0   0:00 /sbin/getty -8 38400 tty6
            1   642   642   642 ?           -1 Ss       0   0:00 cron
            1   643   643   643 ?           -1 Ss       1   0:00 atd
            1   649   621   621 ?           -1 Sl   65534   0:00 /usr/bin/memcached -v -m 1024 -p 11211 -u nobody -l 0.0.0.0
            1   659   659   659 ?           -1 Ssl    108   0:01 /usr/sbin/mysqld
            1   678   678   678 ?           -1 Ss       0   0:00 /usr/sbin/irqbalance
            1   681   681   681 ?           -1 Ss       0   0:00 /usr/sbin/munin-node
            1   699   699   699 ?           -1 Ss       0   0:00 nginx: master process /usr/sbin/nginx
          699   701   699   699 ?           -1 S       33   0:00  \_ nginx: worker process
          699   702   699   699 ?           -1 S       33   0:00  \_ nginx: worker process
          699   703   699   699 ?           -1 S       33   0:00  \_ nginx: worker process
          699   704   699   699 ?           -1 S       33   0:00  \_ nginx: worker process
            1   876   876   876 ?           -1 Ss       0   0:00 /usr/lib/postfix/master
          876   880   876   876 ?           -1 S      106   0:00  \_ pickup -l -t fifo -u
          876   881   876   876 ?           -1 S      106   0:00  \_ qmgr -l -t fifo -u
          876  1622   876   876 ?           -1 S      106   0:00  \_ smtpd -n smtp -t inet -u
          876  1624   876   876 ?           -1 S      106   0:00  \_ tlsmgr -l -t unix -u
          876  1626   876   876 ?           -1 S      106   0:00  \_ trivial-rewrite -n rewrite -t unix -u
          876  1627   876   876 ?           -1 S      106   0:00  \_ cleanup -z -t unix -u
          876  1628   876   876 ?           -1 S      106   0:00  \_ smtp -t unix -u
            1  1071  1071  1071 tty1      1071 Ss+      0   0:00 /sbin/getty -8 38400 tty1
            1  1140   619   619 ?           -1 Sl       0   0:00 /usr/sbin/console-kit-daemon --no-daemon
            1  1604  1601  1601 ?           -1 Sl    1001   0:17 unicorn master -E production_draft -D -c /home/app/app_draft/current/config/system/unicorn.conf.rb                                             
         1604  1608  1601  1601 ?           -1 Sl    1001   0:16  \_ unicorn worker[0] -E production_draft -D -c /home/app/app_draft/current/config/system/unicorn.conf.rb                                          
         1608  1891  1601  1601 ?           -1 S     1001   0:00  |   \_ sh -c /bin/bash -c 'cd /home/app/app_draft/releases/20110916034237 && bundle exec rake qor:job:run JOB=import_stores WORKER_ID=85 RAILS_ENV=production_draft NO_I18N_CACHE=1 --trace'
         1891  1895  1601  1601 ?           -1 S     1001   0:00  |       \_ /bin/bash -c cd /home/app/app_draft/releases/20110916034237 && bundle exec rake qor:job:run JOB=import_stores WORKER_ID=85 RAILS_ENV=production_draft NO_I18N_CACHE=1 --trace
         1895  1896  1601  1601 ?           -1 Rl    1001   0:09  |           \_ ruby /home/app/bundle/ruby/1.9.1/bin/rake qor:job:run JOB=import_stores WORKER_ID=85 RAILS_ENV=production_draft NO_I18N_CACHE=1 --trace
         1604  1611  1601  1601 ?           -1 Sl    1001   0:17  \_ unicorn worker[1] -E production_draft -D -c /home/app/app_draft/current/config/system/unicorn.conf.rb                                          





dmesg


         [13377282.088496] INFO: task ruby:9412 blocked for more than 120 seconds.
         [13377282.088517] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377282.088525] ruby          D ffff880003dec980     0  9412   9408 0x00000004
         [13377282.088532]  ffff8801b9f4fa48 0000000000000282 ffff880100000000 0000000000015980
         [13377282.088538]  ffff8801b9f4ffd8 0000000000015980 ffff8801b9f4ffd8 ffff8801d7778000
         [13377282.088544]  0000000000015980 0000000000015980 ffff8801b9f4ffd8 0000000000015980
         [13377282.088550] Call Trace:
         [13377282.088561]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377282.088569]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377282.088572]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377282.088576]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377282.088580]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377282.088585]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377282.088591]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377282.088597]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377282.088602]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377282.088611]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377282.088617]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377282.088621]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377282.088625]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377282.088629]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377282.088633]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377282.088637]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377282.088641]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377282.088647]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377282.088652]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377282.088656]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377282.088661]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377282.088666]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377282.088669]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377282.088673]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377282.088677]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377282.088681]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377282.088685]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377282.088689]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377282.088692]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377282.088697]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377282.088700] INFO: task ruby:9415 blocked for more than 120 seconds.
         [13377282.088707] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377282.088713] ruby          D ffff880003dec980     0  9415   9408 0x00000004
         [13377282.088719]  ffff8801b9f27a48 0000000000000286 ffff880100000000 0000000000015980
         [13377282.088724]  ffff8801b9f27fd8 0000000000015980 ffff8801b9f27fd8 ffff8801d5f0c4a0
         [13377282.088730]  0000000000015980 0000000000015980 ffff8801b9f27fd8 0000000000015980
         [13377282.088735] Call Trace:
         [13377282.088739]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377282.088743]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377282.088746]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377282.088750]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377282.088753]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377282.088757]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377282.088760]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377282.088764]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377282.088768]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377282.088773]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377282.088776]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377282.088780]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377282.088784]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377282.088788]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377282.088791]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377282.088795]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377282.088799]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377282.088803]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377282.088806]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377282.088810]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377282.088813]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377282.088817]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377282.088820]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377282.088824]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377282.088827]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377282.088830]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377282.088834]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377282.088838]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377282.088841]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377282.088845]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377282.088849] INFO: task ruby:9418 blocked for more than 120 seconds.
         [13377282.088855] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377282.088861] ruby          D ffff880003dec980     0  9418   9408 0x00000004
         [13377282.088866]  ffff8801d7107a48 0000000000000282 ffff8801d71079c8 0000000000015980
         [13377282.088872]  ffff8801d7107fd8 0000000000015980 ffff8801d7107fd8 ffff880125202dc0
         [13377282.088877]  0000000000015980 0000000000015980 ffff8801d7107fd8 0000000000015980
         [13377282.088883] Call Trace:
         [13377282.088886]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377282.088890]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377282.088893]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377282.088897]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377282.088900]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377282.088904]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377282.088908]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377282.088911]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377282.088915]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377282.088920]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377282.088924]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377282.088927]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377282.088931]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377282.088935]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377282.088939]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377282.088943]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377282.088946]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377282.088950]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377282.088954]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377282.088958]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377282.088961]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377282.088964]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377282.088968]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377282.088971]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377282.088974]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377282.088978]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377282.088981]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377282.088985]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377282.088989]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377282.088993]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377282.088996] INFO: task ruby:9424 blocked for more than 120 seconds.
         [13377282.089002] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377282.089008] ruby          D ffff880003dec980     0  9424   9408 0x00000004
         [13377282.089013]  ffff8801d71dfa48 0000000000000286 ffff8801d71df9c8 0000000000015980
         [13377282.089019]  ffff8801d71dffd8 0000000000015980 ffff8801d71dffd8 ffff8800ba94db80
         [13377282.089024]  0000000000015980 0000000000015980 ffff8801d71dffd8 0000000000015980
         [13377282.089030] Call Trace:
         [13377282.089033]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377282.089037]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377282.089040]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377282.089044]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377282.089047]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377282.089051]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377282.089055]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377282.089058]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377282.089062]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377282.089066]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377282.089070]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377282.089074]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377282.089078]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377282.089082]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377282.089086]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377282.089089]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377282.089093]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377282.089097]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377282.089100]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377282.089105]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377282.089108]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377282.089111]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377282.089115]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377282.089118]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377282.089121]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377282.089125]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377282.089128]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377282.089132]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377282.089136]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377282.089140]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377402.088502] INFO: task ruby:9412 blocked for more than 120 seconds.
         [13377402.088525] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377402.088533] ruby          D ffff880003dec980     0  9412   9408 0x00000004
         [13377402.088539]  ffff8801b9f4fa48 0000000000000282 ffff880100000000 0000000000015980
         [13377402.088546]  ffff8801b9f4ffd8 0000000000015980 ffff8801b9f4ffd8 ffff8801d7778000
         [13377402.088552]  0000000000015980 0000000000015980 ffff8801b9f4ffd8 0000000000015980
         [13377402.088558] Call Trace:
         [13377402.088568]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377402.088576]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377402.088580]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377402.088584]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377402.088587]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377402.088593]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377402.088598]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377402.088605]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377402.088610]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377402.088618]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377402.088624]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377402.088627]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377402.088631]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377402.088636]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377402.088640]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377402.088643]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377402.088647]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377402.088653]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377402.088658]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377402.088663]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377402.088666]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377402.088671]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377402.088674]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377402.088678]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377402.088682]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377402.088686]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377402.088690]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377402.088694]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377402.088697]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377402.088702]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377402.088706] INFO: task ruby:9415 blocked for more than 120 seconds.
         [13377402.088712] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377402.088718] ruby          D ffff880003dec980     0  9415   9408 0x00000004
         [13377402.088724]  ffff8801b9f27a48 0000000000000286 ffff880100000000 0000000000015980
         [13377402.088730]  ffff8801b9f27fd8 0000000000015980 ffff8801b9f27fd8 ffff8801d5f0c4a0
         [13377402.088735]  0000000000015980 0000000000015980 ffff8801b9f27fd8 0000000000015980
         [13377402.088741] Call Trace:
         [13377402.088744]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377402.088748]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377402.088751]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377402.088755]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377402.088758]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377402.088762]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377402.088766]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377402.088770]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377402.088774]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377402.088778]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377402.088782]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377402.088785]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377402.088789]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377402.088793]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377402.088797]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377402.088801]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377402.088804]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377402.088808]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377402.088811]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377402.088816]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377402.088819]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377402.088822]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377402.088826]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377402.088829]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377402.088832]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377402.088836]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377402.088839]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377402.088843]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377402.088847]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377402.088851]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377402.088854] INFO: task ruby:9418 blocked for more than 120 seconds.
         [13377402.088859] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377402.088866] ruby          D ffff880003dec980     0  9418   9408 0x00000004
         [13377402.088871]  ffff8801d7107a48 0000000000000282 ffff8801d71079c8 0000000000015980
         [13377402.088877]  ffff8801d7107fd8 0000000000015980 ffff8801d7107fd8 ffff880125202dc0
         [13377402.088882]  0000000000015980 0000000000015980 ffff8801d7107fd8 0000000000015980
         [13377402.088888] Call Trace:
         [13377402.088891]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377402.088895]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377402.088898]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377402.088902]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377402.088905]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377402.088909]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377402.088913]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377402.088916]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377402.088920]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377402.088925]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377402.088928]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377402.088932]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377402.088936]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377402.088940]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377402.088943]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377402.088947]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377402.088951]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377402.088955]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377402.088958]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377402.088963]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377402.088966]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377402.088969]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377402.088973]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377402.088976]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377402.088980]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377402.088983]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377402.088987]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377402.088990]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377402.088994]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377402.088998]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377402.089001] INFO: task ruby:9424 blocked for more than 120 seconds.
         [13377402.089007] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377402.089014] ruby          D ffff880003dec980     0  9424   9408 0x00000004
         [13377402.089018]  ffff8801d71dfa48 0000000000000286 ffff8801d71df9c8 0000000000015980
         [13377402.089024]  ffff8801d71dffd8 0000000000015980 ffff8801d71dffd8 ffff8800ba94db80
         [13377402.089029]  0000000000015980 0000000000015980 ffff8801d71dffd8 0000000000015980
         [13377402.089035] Call Trace:
         [13377402.089038]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377402.089042]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377402.089045]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377402.089049]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377402.089052]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377402.089056]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377402.089060]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377402.089063]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377402.089067]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377402.089072]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377402.089075]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377402.089079]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377402.089083]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377402.089087]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377402.089090]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377402.089094]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377402.089098]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377402.089102]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377402.089106]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377402.089110]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377402.089113]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377402.089117]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377402.089120]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377402.089123]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377402.089126]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377402.089130]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377402.089133]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377402.089137]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377402.089141]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377402.089144]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377402.089149] INFO: task ruby:9985 blocked for more than 120 seconds.
         [13377402.089155] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377402.089161] ruby          D ffff880003dec980     0  9985   9408 0x00000004
         [13377402.089166]  ffff8801d5b39a48 0000000000000282 ffff880100000000 0000000000015980
         [13377402.089171]  ffff8801d5b39fd8 0000000000015980 ffff8801d5b39fd8 ffff8801d7598000
         [13377402.089176]  0000000000015980 0000000000015980 ffff8801d5b39fd8 0000000000015980
         [13377402.089181] Call Trace:
         [13377402.089185]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377402.089189]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377402.089192]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377402.089196]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377402.089199]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377402.089202]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377402.089206]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377402.089210]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377402.089214]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377402.089218]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377402.089222]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377402.089225]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377402.089229]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377402.089233]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377402.089236]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377402.089240]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377402.089243]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377402.089247]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377402.089251]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377402.089255]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377402.089258]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377402.089261]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377402.089264]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377402.089268]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377402.089273]  [<ffffffff8111f439>] ? do_wp_page+0x369/0x900
         [13377402.089277]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377402.089280]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377402.089284]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377402.089288]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377402.089291]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
         [13377522.086012] INFO: task ruby:9412 blocked for more than 120 seconds.
         [13377522.086034] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
         [13377522.086042] ruby          D ffff880003dec980     0  9412   9408 0x00000004
         [13377522.086048]  ffff8801b9f4fa48 0000000000000282 ffff880100000000 0000000000015980
         [13377522.086055]  ffff8801b9f4ffd8 0000000000015980 ffff8801b9f4ffd8 ffff8801d7778000
         [13377522.086061]  0000000000015980 0000000000015980 ffff8801b9f4ffd8 0000000000015980
         [13377522.086067] Call Trace:
         [13377522.086077]  [<ffffffff81100ac0>] ? sync_page+0x0/0x50
         [13377522.086086]  [<ffffffff815a20f3>] io_schedule+0x73/0xc0
         [13377522.086089]  [<ffffffff81100afd>] sync_page+0x3d/0x50
         [13377522.086093]  [<ffffffff815a261a>] __wait_on_bit_lock+0x5a/0xc0
         [13377522.086096]  [<ffffffff81100a97>] __lock_page+0x67/0x70
         [13377522.086102]  [<ffffffff8107f0c0>] ? wake_bit_function+0x0/0x40
         [13377522.086108]  [<ffffffff8110b612>] ? pagevec_lookup+0x22/0x30
         [13377522.086114]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
         [13377522.086119]  [<ffffffff8110cb4e>] invalidate_inode_pages2_range+0x29e/0x2b0
         [13377522.086127]  [<ffffffff81141779>] ? kmem_cache_free+0x99/0x100
         [13377522.086133]  [<ffffffff81241378>] ? fuse_request_free+0x18/0x20
         [13377522.086137]  [<ffffffff81241440>] ? fuse_put_request+0xc0/0xd0
         [13377522.086141]  [<ffffffff8110cb77>] invalidate_inode_pages2+0x17/0x20
         [13377522.086145]  [<ffffffff81248b10>] fuse_finish_open+0x60/0x70
         [13377522.086149]  [<ffffffff81248e99>] fuse_open_common+0x89/0x90
         [13377522.086153]  [<ffffffff81248ea0>] ? fuse_open+0x0/0x20
         [13377522.086156]  [<ffffffff81248eb0>] fuse_open+0x10/0x20
         [13377522.086161]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
         [13377522.086166]  [<ffffffff8125f69f>] ? security_inode_permission+0x1f/0x30
         [13377522.086170]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
         [13377522.086174]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
         [13377522.086180]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
         [13377522.086183]  [<ffffffff8115f526>] do_last+0x86/0x460
         [13377522.086187]  [<ffffffff8116185b>] do_filp_open+0x21b/0x660
         [13377522.086191]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
         [13377522.086195]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
         [13377522.086199]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
         [13377522.086203]  [<ffffffff81151009>] do_sys_open+0x69/0x170
         [13377522.086207]  [<ffffffff81151150>] sys_open+0x20/0x30
         [13377522.086212]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b



http://bugs.gluster.com/show_bug.cgi?id=3011



