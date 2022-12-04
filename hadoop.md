# Hadoop

Below 3 components help us to process large volume of data.

Distributed DataSet - e.g. HDFS - Hadoop Distributed dataSet to store data

Computing framework - e.g. Map Reduce/Spark

Cluster Resource Manager - e.g. Yarn

Hadoop - definition - Big data is high-volume, high-velocity and/or high- variety information assets that demand cost-effective, innovative forms of information processing that enable enhanced insight, decision making, and process automation.

In vertical scalable system we can increase the number of disk in a single high end server, but Hdfs is horizontal scalable where multiple system are connected a cluster.

Hadoop client (edge nodes) -> In large hadoop cluster, we have dedicated few nodes as edge node.There won't have any hadoop services on these edge nodes, but these are used to connect hadoop cluster for day to day activity. There prevent any unnecessary issue/security reason.

**hdfs \<command> \<command options>**

```
few configuration related commands

$ hdfs version
Hadoop 2.6.0-cdh5.7.1
Subversion http://github.com/cloudera/hadoop -r 790551886697a18b03e1ca2142e8a197186ad5ba
Compiled by jenkins on 2017-08-04T14:28Z
Compiled with protoc 2.5.0
From source with checksum 4e6680ae14c539b0458ec74a10c8
This command was run using /opt/cloudera/parcels/CDH-5.7.1-1.cdh5.7.1.p2758.3115/jars/hadoop-common-2.6.0-cdh5.7.1.jar

$ hdfs getconf -namenodes
xxxx009.xxxx.xxx.xxxx.com xxxxx004.xxxx.xxx.xxxxx.com
```

**HDFS Commands Guide :** [http://hadoop.apache.org/docs/r2.7.3/hadoop-project-dist/hadoop-hdfs/HDFSCommands.html](http://hadoop.apache.org/docs/r2.7.3/hadoop-project-dist/hadoop-hdfs/HDFSCommands.html)

[http://hadoop.apache.org/docs/r2.7.3/hadoop-project-dist/hadoop-common/FileSystemShell.html](http://hadoop.apache.org/docs/r2.7.3/hadoop-project-dist/hadoop-common/FileSystemShell.html)

HDFS directory's size

```
hdfs dfs -du -s -h hdfs://dirPath
or
hadoop fs -du -s -h hdfs://dirPath

//-s : total summary size (rather than showing the size of each individual files/dir)
//-h : Formats the sizes in a human-readable fashion rather than a number of bytes.
```

Find text in specified folder's files

```
hadoop fs -cat hdfs://dirPath/* | grep "text"
or
To know which files contain the string "text"
hadoop fs -ls hdfs://dirPath/* | awk '{print $8}' | while read f; do hadoop fs -cat $f | grep text && echo $f ;
```

Hadoop is more than HDFS. Hadoop supports many file system other than hdfs. So Hdfs can be replaced with other file system. Amazon s3, Azure blob storage, Azure data lake storage, linux local file system etc..that means hadoop can access external file systems from hadoop cluster.

So hadoop command are valid for all other supported file systems along with hdfs file system, where as hdfs command only work with hdfs file system.

```
hadoop allow access file path using URI.
scheme://authority/path
e.g. 
local file system - file:// <and no authority>
hdfs -> hdfs://xxxx-xxxxx-xxx/tmp/

if default is defined than no need to specify scheme.
```

Find Sample data from hdfs file.

```
$ hadoop fs -cat /your/file | head
The head and tail commands on Linux display the first 10 and last 10 lines respectively. 
But, the output of these two commands is not randomly sampled.
shuffle 'shuf' command helps to generate random permutations of input lines.

$ hadoop fs -cat /your/file | shuf -n 50
```
