MapReduce, Yarn and pseudodistributed mode(Hadoop)

1. Configure ssh-keys so that password isn't asked everytime.
ssh-keygen -t dsa -P '' -f ~/.ssh/id_dsa
cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys
chmod 0600 ~/.ssh/authorized_keys

2.core-site.xml:

<configuration>

    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://localhost:9000</value>
    </property>

</configuration>

3. hdfs-site.xml:

<configuration>

    <property>
        <name>dfs.replication</name>
        <value>1</value>
    </property>
</configuration>

4. yarn-site.xml:

<configuration>

    <property>
        <name>yarn.nodemanager.aux-services</name>
        <value>mapreduce_shuffle</value>
    </property>

    <property>
        <name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
        <value>org.apache.hadoop.mapred.ShuffleHandler</value>
    </property>

</configuration>

5. mapred-site.xml:

<configuration>

    <property>
        <name>mapreduce.framework.name</name>
        <value>yarn</value>
    </property>

</configuration>

--- other options like local, yarn are available.

 
