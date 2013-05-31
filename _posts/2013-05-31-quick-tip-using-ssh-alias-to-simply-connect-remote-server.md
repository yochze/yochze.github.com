---
layout: post
title: Using SSH alias to simplify connection to remote servers
comments: true
---

Connecting remote servers using SSH is a fundamental part of my daily tasks. Whether it's connecting to a EC2 instance or managing the VPS of a certain app, it is all taken care of through the SSH protocol.

The SSH protocol allows your to login and connect to a remote server and execute commands on that server. 

Normally, I have used the following to connect a remote server

	$ ssh -i ~/cert.pem ec2-user@ec2-123-123-123.amazonaws.com

This is terribly long, and in case you have several servers to manage - it is also very confusing. So I was looking a way to make it easier and simpler.

I have found that adding my servers to a `config` file in the `.ssh` directory might do the trick. Here is what I have done:

	$ touch ~/.ssh/config # 
	$ vim ~/.ssh/config

Inside the config file, I added the info mentioned below. The info represents a single connection to a remote server. It requires an alias, the server address, the username and the pem.

	Host: webbing
	HostName: ec2-user@ec2-123-123-123.amazonaws.com 
	User: ec2-user
	IdentifyFile: ~/cert.pem

Now, the `connecting` command has shortned to 

	$ ssh webbing
