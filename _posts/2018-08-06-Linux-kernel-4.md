---
layout: post
title: Dialogues on linux kernel-3
subtitle: Building linux kernel source from scratch.
tags: [tutorial, software, linux, kernel, os]
---
### Architecture of Linux kernel
![Linux-Architecture](https://i.pinimg.com/originals/a4/76/e5/a476e5ac785fa192712b24316bfaf3c3.gif){:class="img-responsive"}
### Before We start
This series is neither totally theoritical nor totally hands-on. It is amalgammation of both. Just the way I think. You will not become expert which should be implied.  
### ?
Command prefix "hdfs ":

| Commands | Description |
| :------ | :----------------------- |
| fs –help ls | lists the usage information along with the options to use the command |
| fs –ls –R /user/username | Returns all the available files and recursively lists all the subdirectories under /user/username |
| fs –mkdir /user/username/directory-name | create a new directory |
| fs –copyFromLocal Sample1.txt /user/username/destination-address | copy from local filesystem to hdfs |
| fs –put Sample2.txt /user/username/destination-address | uploads a single file or multiple source files from local file system to hadoop distributed file system |
| fs –moveFromLocal Sample1.txt /user/username/destination-address | deletes original and copy |
| fs –du /user/username/destination-address | HDFS disk usage command |
| fs –df | Display disk usage of current hadoop distributed file system |
| fs –expunge | empties the trash by deleting all the files and directories |
###### There a lot of other command similar to unix file system with hadoop fs prefixed.
Command prefix "hdfs ":

| Commands | Description |
| :------ | :----------------------- |
| classpath --glob | expands wildcard *I don't know what that is* |
| classpath --jar | write classpath as manifest in jar named path |
| classpath -h | print help |

###### It checks file system integrity
Command prefix "hdfs fcsk ":

| Commands | Description |
| :------ | :----------------------- |
|-delete | Delete corrupted files. |
| -files | Print out files being checked. |
| -files -blocks | Print out the block report |
| -files -blocks -locations | Print out locations for every block. |
| -files -blocks -racks | Print out network topology for data-node locations. |
| -files -blocks -replicaDetails | Print out each replica details. |
| -files -blocks -upgradedomains | Print out upgrade domains for every block. |
| -includeSnapshots | Include snapshot data if the given path indicates a snapshottable directory or there are snapshottable directories under it. |
|-list-corruptfileblocks | Print out list of missing blocks and files they belong to. |
| -move | Move corrupted files to /lost+found. |
| -openforwrite | Print out files opened for write. |
| -storagepolicies | Print out storage policy summary for the blocks. |
| -maintenance | Print out maintenance state node details. |
| -blockId | Print out information about the block. |
