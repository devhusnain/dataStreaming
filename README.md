# dataStreaming

#How To Install Docker Compose on Ubuntu 20.04
Now that we know what Docker Compose is, let's dive into installing the latest Docker Compose on Ubuntu. We'll borrow from the official Docker Compose Linux install docs, but we'll streamline the process here so you can hit the ground running with this demo project. Once Docker Compose is installed on our Ubuntu 20.04 system, we'll use it to run a simple multi-service demo app.

#Prerequisites
Access to the terminal of an Ubuntu 20.04 (or similar) system
sudo/root privileges
#Step 1: Add Docker's Repository To Your System
The recommended way to install Docker Compose and related packages from Docker is to add Docker's repository to your system's list of repos. Adding Docker's repo will allow you to download and update the latest packages using the apt package manager.

To begin, update your package list:<br>

```bash 
apt update -y
```
<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-26-20.png"/>
Next, you'll need these four packages to allow apt to work with HTTPS-based repositories:

ca-certificates - A package that verifies SSL/TLS certificates.
curl - A popular data transfer tool that supports multiple protocols including HTTPS.
gnupg - An open source implementation of the Pretty Good Privacy (PGP) suite of cryptographic tools.
lsb-release - A utility for reporting Linux Standard Base (LSB) versions.
Use this command to install those packages:<br>

```bash 
apt install ca-certificates curl gnupg lsb-release
```
Output will look similar to:Install prerequisites

Make a directory for Docker's GPG key:<br>

```bash 
mkdir /etc/apt/demokeyrings
```
Use curl to download Docker's keyring and pipe it into gpg to create a GPG file so apt trusts Docker's repo:<br>

 ```bash 
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/demokeyrings/demodocker.gpg
```
 
Add the Docker repo to your system with this command:<br>
```bash 
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/demokeyrings/demodocker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```
The output should look similar to:Add official Docker repo<br>

#Step 2: Install Docker Compose And Related Packages<br>
Now that you added Docker's repo, update your package lists again:<be>

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-27-18.png"/>

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-30-46.png"/>



Next, install Docker-CE (Community Edition), the Docker-CE CLI, the containerd runtime, and Docker Compose with this command:<br>

```bash
apt update -y
```

```bash 
apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Output should look similar to:Install Docker

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-31-20.png"/>
You can verify Docker-CE, the Docker-CE CLI, containerd, and Docker Compose are installed by checking their versions with these commands:<br>

```bash 
docker --version; docker compose version;ctr version
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-31-43.png"/>






Apache Nifi comes to mind if you are looking for a simple, but robust, tool to process data from various sources. 
In short, Apache NiFi is a tool to process and distribute data. Its intuitive UI supports routing definitions, a variety of connectors 
(in/out), and many built-in processors. All these features combined together make it a suitable optional platform for our use case.

#how to run nifi on ec2
```bash
https://hub.docker.com/r/apache/nifi/
```


https://hub.docker.com/r/apache/nifi-...

Step -1: Pull docker Image

```bash 
docker pull apache/nifi:latest
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-08-23.png"/>

Step 2: Create a container

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-22-17.png?token=GHSAT0AAAAAACF4RWELY5HNSKB5JV2MEVJMZGMDPOQ"/>

Name my container (I named it devnifi)

Controlling the port, and mapped to 8443

Being able to see the loading and standard output of Nifi

Create a shared volume between my host (shared-directory) and the container (ls-target)

```bash 
docker run --name devnifi -p 8081:8081 -d -e NIFI_WEB_HTTP_PORT='8081' apache/nifi:latest
```


Step 3: Verify using logs

```bash 
docker logs -f devnifi
```

Step 4: Pull Nifi registry and create container 

```bash 
docker pull apache/nifi-registry
```

then run the registry which managing version control for Nifi flow.

```bash 
docker run --name nifi-registry -p 18080:18080 -d apache/nifi-registr
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-29-01.png?token=GHSAT0AAAAAACF4RWEKIDPNLURUGSABYGWEZGMDWIQ"/>

Step 5: Validation

visit
```bash 
http://publicIP:8081/nifi
```
 ```bash
http://publicIP:18080/nifi-registry
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-30-57.png?token=GHSAT0AAAAAACF4RWEK7IAE45RY7ZBJFUFIZGMDUVA"/>

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-30-45.png?token=GHSAT0AAAAAACF4RWEKH5BTZPKZT277UFEEZGMDUUQ"/>

#how to import template to nifi
      go to ```http://publicIP:8081/nifi```
      Download template Joshua-final-stocks-nifi.xml from this repo
      click upload template 
      select template and upload it.
      
<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2002-23-55.png?token=GHSAT0AAAAAACF4RWEKMU7ZNBHUJYEJOUBYZGMFGUQ"/>




#about MySQL 
#Step1: Pull MySQL Image from Docker Hub<br>
First, pull MySQL from Docker Hub to the local system by executing the provided command in terminal <br>

#Step2: Build and Run MySQL Container <br>
Then, create and run the MySQL container using the MySQL image through the “docker run -td –name mysql -e MYSQL_ROOT_PASSWORD=<password> mysql:latest” command:<br>

The “–name” option defines the name for the container i.e., “mySql-cont”.
The “-e MYSQL_ROOT_PASSWORD” specifies the root password to “mysql123”.
The “mysql:latest” is the latest MySQL Docker image to use for the container:<br>

#Step3: View Running MySQL Container
Write out the below-listed command to verify whether the MySQL container is running or not<br>

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2002-08-13.png?token=GHSAT0AAAAAACF4RWELO3PQF2Y5P3OBX5PKZGMFABQ"/>

#Step4: Access MySQL Container
After that, use the “docker exec -it mysql bash ” command with the container name to open the Bash shell inside the running MySQL container:
The above-stated command has opened the Bash shell and now users can execute MySQL commands within the running MySQL container.<br>

#Step5: Connect to MySQL Database
Next, connect to the MySQL database as the root user via the following command and enter the password in an interactive mode:<br>

#Step6: Create a Database in MySQL
To create a database in MySQL, execute the “CREATE DATABASE stream_db;” command:

CREATE DATABASE stream_db;


<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2002-09-32.png?token=GHSAT0AAAAAACF4RWEKU7Q4PSMD5BR34BKWZGMFAHA"/>





#Running Apache Airflow container on ec2

Older versions of docker-compose do not support all the features required by the Airflow docker-compose.yaml file, so double check that your version meets the minimum version requirements.

The default amount of memory available for Docker on macOS is often not enough to get Airflow up and running. If enough memory is not allocated, it might lead to the webserver continuously restarting. You should allocate at least 4GB memory for the Docker Engine (ideally 8GB).

You can check if you have enough memory by running this command:

```bash 
docker run --rm "debian:bullseye-slim" bash -c 'numfmt --to iec $(echo $(($(getconf _PHYS_PAGES) * $(getconf PAGE_SIZE))))'
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-47-56.png"/>

Fetching docker-compose.yaml
To deploy Airflow on Docker Compose, you should fetch docker-compose.yaml.
```bash 
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.6.3/docker-compose.yaml'
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-51-06.png"/>

Initializing Environment
Before starting Airflow for the first time, you need to prepare your environment, i.e. create the necessary files, directories and initialize the database.

Setting the right Airflow user
On Linux, the quick-start needs to know your host user id and needs to have group id set to 0. Otherwise the files created in dags, logs and plugins will be created with root user ownership. You have to make sure to configure them for the docker-compose:


```bash
mkdir -p ./dags ./logs ./plugins ./config
```

```bash 
echo -e "AIRFLOW_UID=$(id -u)" > .env
```

For other operating systems, you may get a warning that AIRFLOW_UID is not set, but you can safely ignore it. You can also manually create an .env file in the same folder as docker-compose.yaml with this content to get rid of the warning:

```bash 
AIRFLOW_UID=50000
```

Initialize the database
On all operating systems, you need to run database migrations and create the first user account. To do this, run.

```bash 
docker compose up airflow-init
```

Running Airflow
Now you can start all services:

```bash
docker compose up
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-58-19.png"/>

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2002-28-55.png"/>
see the documentation:

https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html


#How to deploy fastapi using nginx

clone the repo by using this command
```bash 
git clone https://github.com/devhusnain/dataStreaming.git
```
use these commands to install python-pip and requirements for fastapi 
```bash 
sudo apt-get update
```
```bash 
sudo apt install python3-pip
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2001-56-07.png"/>


```bash 
pip3 install -r requirements.txt
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2002-01-00.png"/>

```bash 
sudo apt install nginx
```

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2002-06-47.png"/>



```bash
cd /etc/nginx/sites-enabled/
```


```bash
sudo nano fastapi_nginx
```

note: please change the public ip to ur ip
<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2002-08-47.png"/>


```bash
 sudo service nginx restart
```
cd path to your fastapi


```python 
python3 -m uvicorn api:app
```

You can now access you fastapi via public ip 
<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-06%2002-36-19.png"/>


# MSK service for kafka

From the Debezium website ``` https://debezium.io/releases/2.3/ ```, I download the MySQL connector plugin for the latest stable release. Because MSK Connect accepts custom plugins in ZIP or JAR format, I convert the downloaded archive to ZIP format and keep the JARs files in the main directory:

``` json
tar xzf debezium-connector-mysql-2.3.3.Final-plugin.tar.gz
```

```json
cd debezium-connector-mysql
```
```json
zip -9 ../debezium-connector-mysql-2.3.3.zip *
```
```json
cd ..
```

you can manully download this file  debezium-connector-mysql-2.3.3.Final-plugin.tar.gz  and create the zip file from it.



Then, upload the custom plugin to an Amazon Simple Storage Service (Amazon S3) bucket in the same AWS Region I am using for MSK Connect:

pic

On the Amazon MSK console there is a new MSK Connect section. I look at the connectors and choose Create connector. Then, I create a custom plugin and browse my S3 buckets to select the custom plugin ZIP file I uploaded before.

pic 

I enter a name and a description for the plugin and then choose Next.

pic


Now that the configuration of the custom plugin is complete, I start the creation of the connector. I enter a name and a description for the connector.



I have the option to use a self-managed Apache Kafka cluster or one that is managed by MSK. I select one of my MSK cluster that is configured to use IAM authentication. The MSK cluster I select is in the same virtual private cloud (VPC) as my Aurora database. To connect, the MSK cluster and Aurora database use the default security group for the VPC. For simplicity, I use a cluster configuration with auto.create.topics.enable set to true.

pic





# Msk connector










```json
cat >>  ~/.bash_profile
export PATH=~/kafka_2.12-2.8.1/bin:$PATH                                        
export CLASSPATH=/home/ubuntu/aws-msk-iam-auth-1.1.9-all.jar
export BOOTSTRAP_SERVERS=b-1.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098,b-2.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098,b-3.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098
```

```json

connector.class=io.debezium.connector.mysql.MySqlConnector
database.history.producer.sasl.mechanism=AWS_MSK_IAM
database.history.producer.sasl.jaas.config=software.amazon.msk.auth.iam.IAMLoginModule required;
database.user=admin
database.server.id=123456
tasks.max=1
database.history.consumer.sasl.jaas.config=software.amazon.msk.auth.iam.IAMLoginModule required;
database.history.producer.security.protocol=SASL_SSL
database.history.kafka.topic=dbhistory.stream_db
database.history.kafka.bootstrap.servers=b-1.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098,b-2.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098,b-3.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098
database.server.name=stock-server
database.history.producer.sasl.client.callback.handler.class=software.amazon.msk.auth.iam.IAMClientCallbackHandler
schema.history.internal.kafka.bootstrap.servers=b-1.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098,b-2.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098,b-3.msk.ciosr2.c2.kafka.us-east-1.amazonaws.com:9098
database.history.consumer.sasl.client.callback.handler.class=software.amazon.msk.auth.iam.IAMClientCallbackHandler
database.history.consumer.security.protocol=SASL_SSL
database.port=3306
include.schema.changes=true
topic.prefix=stream_db_
schema.history.internal.kafka.topic=stream_db_internal
database.hostname=database-2-instance-1.cvyohyithmox.us-east-1.rds.amazonaws.com
database.password=12345678
database.history.consumer.sasl.mechanism=AWS_MSK_IAM
database.include.list=stream_db

```
Some of these settings are generic and should be specified for any connector. For example:

connector.class is the Java class of the connector.
tasks.max is the maximum number of tasks that should be created for this connector.
Other settings are specific to the Debezium MySQL connector:

The database.hostname contains the writer instance endpoint of my Aurora database.
The database.server.name is a logical name of the database server. It is used for the names of the Kafka topics created by Debezium.
The database.include.list contains the list of databases hosted by the specified server.
The database.history.kafka.topic is a Kafka topic used internally by Debezium to track database schema changes.
The database.history.kafka.bootstrap.servers contains the bootstrap servers of the MSK cluster.
The final eight lines (database.history.consumer.* and database.history.producer.*) enable IAM authentication to access the database history topic.

In Connector capacity, I can choose between autoscaled or provisioned capacity. For this setup, I choose provisioned and leave all other settings at their defaults.

For Worker configuration, you can use the default one provided by Amazon MSK or provide your own configuration. In my setup, I use the default one.

In Access permissions, I create a IAM role. In the trusted entities, I add kafkaconnect.amazonaws.com to allow MSK Connect to assume the role.

The role is used by MSK Connect to interact with the MSK cluster and other AWS services. For my setup, I add:

Permissions to write logs to a Amazon CloudWatch log group I created earlier.
Permissions to authenticate to my MSK cluster through IAM.
The Debezium connector needs access to the cluster configuration to find the replication factor to use to create the history topic. For this reason, I add to the permissions policy the kafka-cluster:DescribeClusterDynamicConfiguration action (equivalent Apache Kafka’s DESCRIBE_CONFIGS cluster ACL).

Depending on your configuration, you might need to add more permissions to the role (for example, in case the connector needs access to other AWS resources such as an S3 bucket). If that is the case, you should add permissions before creating the connector.

pics



I download a binary distribution of Apache Kafka and extract the archive in the home directory:

$ tar xvf kafka_2.13-2.7.1.tgz
To use IAM to authenticate with the MSK cluster, I follow the instructions in the Amazon MSK Developer Guide to configure clients for IAM access control. I download the latest stable release of the Amazon MSK Library for IAM:

```json
wget https://github.com/aws/aws-msk-iam-auth/releases/download/1.1.0/aws-msk-iam-auth-1.1.0-all.jar
```
In the ~/kafka_2.13-2.7.1/config/ directory I create a client-config.properties file to configure a Kafka client to use IAM authentication:

```json
# Sets up TLS for encryption and SASL for authN.
security.protocol = SASL_SSL

# Identifies the SASL mechanism to use.
sasl.mechanism = AWS_MSK_IAM

# Binds SASL client implementation.
sasl.jaas.config = software.amazon.msk.auth.iam.IAMLoginModule required;

# Encapsulates constructing a SigV4 signature based on extracted credentials.
# The SASL client bound by "sasl.jaas.config" invokes this class.
sasl.client.callback.handler.class = software.amazon.msk.auth.iam.IAMClientCallbackHandler
```






In the third terminal connection, I install a MySQL client using the MariaDB package and connect to the Aurora database:

```json
$ sudo apt install mariadb
$ mysql -h database-2-instance-1.cvyohyithmox.us-east-1.rds.amazonaws.com -u admin -p

```

From this connection, I create the stock-database and a table for my stock:

```
CREATE TABLE stock (
    record_id INT NOT NULL AUTO_INCREMENT,
    time DATETIME NOT NULL,
    open FLOAT NOT NULL,
    high FLOAT NOT NULL,
    low FLOAT NOT NULL,
    close FLOAT NOT NULL,
    volume FLOAT NOT NULL,
    symbol VARCHAR(40),
    event_time DATETIME DEFAULT NOW(),
    PRIMARY KEY (record_id)
);
```


These database changes are captured by the Debezium connector managed by MSK Connect and are streamed to the MSK cluster. In the first terminal, consuming the topic with schema changes, I see the information on the creation of database and table:
