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

prefix hdfs getconf:

| Commands | Description |
| :------ | :----------------------- |
| -namenodes | gets list of namenodes in the cluster. |
| -secondaryNameNodes | gets list of secondary namenodes in the cluster. |
| -backupNodes | gets list of backup nodes in the cluster. |
| -includeFile | gets the include file path that defines the datanodes that can join the cluster. |
| -excludeFile | gets the exclude file path that defines the datanodes that need to decommissioned. |
| -nnRpcAddresses | gets the namenode rpc addresses |
| -confKey key | gets a specific key from the configuration |

prefix hdfs groups:
| Commands | Description |
| :------ | :----------------------- |
|  username | Returns the group information given one or more usernames. |

prefix hdfs balancer:

| Commands | Description |
| :------ | :----------------------- |
| -policy policy | datanode (default): Cluster is balanced if each datanode is balanced.blockpool: Cluster is balanced if each block pool in each datanode is balanced. |
| -threshold threshold | Percentage of disk capacity. This overwrites the default threshold. |
| -exclude -f hosts-file comma-separated list of hosts | Excludes the specified datanodes from being balanced by the balancer. |
| -include -f <hosts-file> comma-separated list of hosts | Includes only the specified datanodes to be balanced by the balancer. |
| -source -f <hosts-file> comma-separated list of hosts | Pick only the specified datanodes as source nodes. |
| -blockpools comma-separated list of blockpool ids | The balancer will only run on blockpools included in this list. |
| -idleiterations <iterations> | Maximum number of idle iterations before exit. This overwrites the default idleiterations(5). |
| -runDuringUpgrade | Whether to run the balancer during an ongoing HDFS upgrade. This is usually not desired since it will not affect used space on over-utilized machines. |
| -h | Display the tool usage and help information and exit. |

### Generic options
Prefix hdfs :

| Commands | Description |
| :------ | :----------------------- |
| -archives comma separated list of archives | Specify comma separated archives to be unarchived on the compute machines. Applies only to job.  |
| -conf configuration file | Specify an application configuration file.  |
| -D property=value | Use value for given property.  |
|-files comma separated list of files | Specify comma separated files to be copied to the map reduce cluster. Applies only to job. |
| -fs file:/// or hdfs://namenode:port | Specify default filesystem URL to use. Overrides ‘fs.defaultFS’ property from configurations. |
| -jt local or resourcemanager:port | Specify a ResourceManager. Applies only to job. |
| -libjars comma seperated list of jars | Specify comma separated jar files to include in the classpath. Applies only to job. |

##### [See more](http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/CommandsManual.html#Generic_Options)
#### Cacheadmin

* hdfs cacheadmin [-addDirective -path <path> -pool <pool-name> [-force] [-replication <replication>] [-ttl <time-to-live>]]
* hdfs cacheadmin [-modifyDirective -id <id> [-path <path>] [-force] [-replication <replication>] [-pool <pool-name>] [-ttl <time-to-live>]]
* hdfs cacheadmin [-listDirectives [-stats] [-path <path>] [-pool <pool>] [-id <id>]]
* hdfs cacheadmin [-removeDirective <id>]
* hdfs cacheadmin [-removeDirectives -path <path>]
* hdfs cacheadmin [-addPool <name> [-owner <owner>] [-group <group>] [-mode <mode>] [-limit <limit>] [-maxTtl <maxTtl>]]
* hdfs cacheadmin [-modifyPool <name> [-owner <owner>] [-group <group>] [-mode <mode>] [-limit <limit>] [-maxTtl <maxTtl>]]
* hdfs cacheadmin [-removePool <name>]
* hdfs cacheadmin [-listPools [-stats] [<name>]]
* hdfs cacheadmin [-help <command-name>]
