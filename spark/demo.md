local单机模式：
结果xshell可见：
./bin/spark-submit --class org.apache.spark.examples.SparkPi --master local[1] ./lib/spark-examples-1.3.1-hadoop2.4.0.jar 100

standalone集群模式：
需要的配置项
1, slaves文件
2, spark-env.sh
export JAVA_HOME=/usr/soft/jdk1.7.0_71
export SPARK_MASTER_IP=spark001
export SPARK_MASTER_PORT=7077
export SPARK_WORKER_CORES=1
export SPARK_WORKER_INSTANCES=1
export SPARK_WORKER_MEMORY=1g

standalone集群模式：
之client模式：
结果xshell可见：
./bin/spark-submit --class org.apache.spark.examples.SparkPi --master spark://spark001:7077 --executor-memory 1G --total-executor-cores 1 ./lib/spark-examples-1.3.1-hadoop2.4.0.jar 100


standalone集群模式：
之cluster模式：
结果spark001:8080里面可见！
./bin/spark-submit --class org.apache.spark.examples.SparkPi --master spark://spark001:7077 --deploy-mode cluster --supervise --executor-memory 1G --total-executor-cores 1 ./lib/spark-examples-1.3.1-hadoop2.4.0.jar 100

Yarn集群模式：
需要的配置项
1, spark-env.sh
export HADOOP_CONF_DIR=$HADOOP_INSTALL/etc/hadoop
export YARN_CONF_DIR=$HADOOP_INSTALL/etc/hadoop
export SPARK_HOME=/usr/hadoopsoft/spark-1.3.1-bin-hadoop2.4
export SPARK_JAR=/usr/hadoopsoft/spark-1.3.1-bin-hadoop2.4/lib/spark-assembly-1.3.1-hadoop2.4.0.jar
export PATH=$SPARK_HOME/bin:$PATH
2, ~/.bash_profile
配置好hadoop环境变量

Yarn集群模式：
client模式：
结果xshell可见：
./bin/spark-submit --class org.apache.spark.examples.SparkPi --master yarn-client --executor-memory 1G --num-executors 1 ./lib/spark-examples-1.3.1-hadoop2.4.0.jar 100

Yarn集群模式：
cluster模式：
结果spark001:8088里面可见！
./bin/spark-submit --class org.apache.spark.examples.SparkPi --master yarn-cluster --executor-memory 1G --num-executors 1 ./lib/spark-examples-1.3.1-hadoop2.4.0.jar 100
