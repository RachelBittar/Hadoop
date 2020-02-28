# Hadoop

Execution

The following instructions are to run a MapReduce job locally. If you want to execute a job on YARN, see YARN on Single Node.

Format the filesystem:
$ bin/hdfs namenode -format

Start NameNode daemon and DataNode daemon:
$ sbin/start-dfs.sh

The hadoop daemon log output is written to the $HADOOP_LOG_DIR directory (defaults to $HADOOP_HOME/logs).

Browse the web interface for the NameNode; by default it is available at:

NameNode - http://localhost:50070/
Make the HDFS directories required to execute MapReduce jobs:

$ bin/hdfs dfs -mkdir /user
$ bin/hdfs dfs -mkdir /user/<username>

Copy the input files into the distributed filesystem:

$ bin/hdfs dfs -put etc/hadoop input
Run some of the examples provided:

$ bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.3.jar grep input output 'dfs[a-z.]+'

Examine the output files: Copy the output files from the distributed filesystem to the local filesystem and examine them:

$ bin/hdfs dfs -get output output
$ cat output/*

or

View the output files on the distributed filesystem:
$ bin/hdfs dfs -cat output/*
When you’re done, stop the daemons with:

$ sbin/stop-dfs.sh