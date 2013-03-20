---
layout: post
title: Open closed company network with ssh out through http proxy
tags: main
gplus: https://plus.google.com/109226469261450457142/posts/VRo52YWhM46
---

### The problem
You get the situation that company are paranoid that they won't use Amazon EC2 or any other cloud services or rented servers, Because it's not safe to use any others servers except the ones that physically located in their own office. These companies normally their network are closed, computers inside network has to go through a http proxy server to check internet, and they block whatever services they don't like.

And here is the problem, How do you deploy system to the closed server in their office. and update your system frequently to reflect bug fixes and improvements, We know that system can't be perfect just for one release, you have to be continually improve your system with users feedback.

But you can't go into their office to upgrade system for every small fix. It won't be efficient, and not the things we do in this internet age. except the first time after the server ready, you have to go their to configure it initially.

### ssh for the rescue
How to solve is you make a tunnel to the outside server you have fully control, when you configure their system initially, and keep that tunnel running and create a cron job to check that tunnel process is running and start it if it's gone. Here is how to start a tunnel to other server.

	ssh -CnN -R 9999:localhost:22 sasaki@theserver.youhavecontrol.com -p 443

- Make sure the sshd service is running at 443 on your outside server, normally company will block other ports then 80, or 443.
- -C: Requests compression of all data
- -n: Redirects stdin from /dev/null (actually, prevents reading from stdin).  This must be used when ssh is run in the background.
- -N: Do not execute a remote command.  This is useful for just forwarding ports, Don't login to the other server.
- -R: do remote port forwarding

You can do `man ssh` to check all the details of these options.

After done this, You can ssh in to theserver.youhavecontrol.com:

	ssh sasaki@theserver.youhavecontrol.com -p 443

Then you ssh into the server inside the company:

	ssh username@localhost -p 9999

What? it doesn't work, the server has to go through http proxy to access internet.

### corkscrew enable you ssh through http proxy

Go http://www.agroman.net/corkscrew/ to download the latest version of corkscrew:

    curl -O http://www.agroman.net/corkscrew/corkscrew-2.0.tar.gz
    tar -xzvf corkscrew-2.0.tar.gz
    ./configure
    make && sudo make install

Then go to ~/.ssh/config

    Host * 
      ProxyCommand /usr/local/bin/corkscrew 10.0.88.88 8080 %h %p
    
Note that 10.0.88.88 and 8080 is the companies' http proxy and here is saying any ssh will use corkscrew command and go through that http proxy

### Trouble shooting
1. I have used 80 port at theserver.youhavecontrol.com server, But somehow it doesn't work, and ssh gives these, change to port 443 worked.

		OpenSSH_5.3p1, OpenSSL 1.0.0-fips 29 Mar 2010
		debug1: Reading configuration data /home/redhat/.ssh/config
		debug1: Applying options for *
		debug1: Reading configuration data /etc/ssh/ssh_config
		debug1: Applying options for *
		debug1: Executing proxy command: exec /usr/local/bin/corkscrew 10.0.88.88 8080 github.com 22
		debug1: permanently_drop_suid: 501
		debug1: identity file /home/redhat/.ssh/identity type -1
		debug1: identity file /home/redhat/.ssh/id_rsa type 1
		debug1: identity file /home/redhat/.ssh/id_dsa type -1
		Proxy could not open connnection to github.com: Forbidden
		ssh_exchange_identification: Connection closed by remote host


