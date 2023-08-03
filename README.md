# dataStreaming

Apache Nifi comes to mind if you are looking for a simple, but robust, tool to process data from various sources. 
In short, Apache NiFi is a tool to process and distribute data. Its intuitive UI supports routing definitions, a variety of connectors 
(in/out), and many built-in processors. All these features combined together make it a suitable optional platform for our use case.

#how to run nifi on ec2
https://hub.docker.com/r/apache/nifi/


https://hub.docker.com/r/apache/nifi-...

Step -1: Pull docker Image

docker pull apache/nifi:latest

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-08-23.png?token=GHSAT0AAAAAACF4RWELLD2WGKLPRMAKUNPMZGMFQ6A"/>

Step 2: Create a container

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-22-17.png?token=GHSAT0AAAAAACF4RWELY5HNSKB5JV2MEVJMZGMDPOQ"/>

Name my container (I named it devnifi)
Controlling the port, and mapped to 8443
Being able to see the loading and standard output of Nifi
Create a shared volume between my host (shared-directory) and the container (ls-target)
docker run --name devnifi -p 8081:8081 -d -e NIFI_WEB_HTTP_PORT='8081' apache/nifi:latest


Step 3: Verify using logs

docker logs -f devnifi

Step 4: Pull Nifi registry and create container 

docker pull apache/nifi-registry

then run the registry which managing version control for Nifi flow.

docker run --name nifi-registry -p 18080:18080 -d apache/nifi-registry

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-29-01.png?token=GHSAT0AAAAAACF4RWEKIDPNLURUGSABYGWEZGMDWIQ"/>

Step 5: Validation

visit http://publicIP:8081/nifi
      http://publicIP:18080/nifi-registry

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-30-57.png?token=GHSAT0AAAAAACF4RWEK7IAE45RY7ZBJFUFIZGMDUVA"/>

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-30-45.png?token=GHSAT0AAAAAACF4RWEKH5BTZPKZT277UFEEZGMDUUQ"/>

#how to import template to nifi
      go to http://publicIP:8081/nifi
      Download template Joshua-final-stocks-nifi.xml from this repo
      click upload template
      
<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2002-23-55.png?token=GHSAT0AAAAAACF4RWEKMU7ZNBHUJYEJOUBYZGMFGUQ"/>

select template and upload it.


#about MySQL 
#Step1: Pull MySQL Image from Docker Hub
First, pull MySQL from Docker Hub to the local system by executing the provided command in terminal 
#Step2: Build and Run MySQL Container
Then, create and run the MySQL container using the MySQL image through the “docker run -td –name mysql -e MYSQL_ROOT_PASSWORD=<password> mysql:latest” command:
The “–name” option defines the name for the container i.e., “mySql-cont”.
The “-e MYSQL_ROOT_PASSWORD” specifies the root password to “mysql123”.
The “mysql:latest” is the latest MySQL Docker image to use for the container:
#Step3: View Running MySQL Container
Write out the below-listed command to verify whether the MySQL container is running or not

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2002-08-13.png?token=GHSAT0AAAAAACF4RWELO3PQF2Y5P3OBX5PKZGMFABQ"/>

#Step4: Access MySQL Container
After that, use the “docker exec -it mysql bash ” command with the container name to open the Bash shell inside the running MySQL container:
The above-stated command has opened the Bash shell and now users can execute MySQL commands within the running MySQL container.
#Step5: Connect to MySQL Database
Next, connect to the MySQL database as the root user via the following command and enter the password in an interactive mode:
#Step6: Create a Database in MySQL
To create a database in MySQL, execute the “CREATE DATABASE stream_db;” command:

CREATE DATABASE stream_db;


<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2002-09-32.png?token=GHSAT0AAAAAACF4RWEKU7Q4PSMD5BR34BKWZGMFAHA"/>

