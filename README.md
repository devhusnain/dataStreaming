# dataStreaming

#How To Install Docker Compose on Ubuntu 20.04
Now that we know what Docker Compose is, let's dive into installing the latest Docker Compose on Ubuntu. We'll borrow from the official Docker Compose Linux install docs, but we'll streamline the process here so you can hit the ground running with this demo project. Once Docker Compose is installed on our Ubuntu 20.04 system, we'll use it to run a simple multi-service demo app.

#Prerequisites
Access to the terminal of an Ubuntu 20.04 (or similar) system
sudo/root privileges
#Step 1: Add Docker's Repository To Your System
The recommended way to install Docker Compose and related packages from Docker is to add Docker's repository to your system's list of repos. Adding Docker's repo will allow you to download and update the latest packages using the apt package manager.

To begin, update your package list:

apt update -y
Next, you'll need these four packages to allow apt to work with HTTPS-based repositories:

ca-certificates - A package that verifies SSL/TLS certificates.
curl - A popular data transfer tool that supports multiple protocols including HTTPS.
gnupg - An open source implementation of the Pretty Good Privacy (PGP) suite of cryptographic tools.
lsb-release - A utility for reporting Linux Standard Base (LSB) versions.
Use this command to install those packages:

apt install ca-certificates curl gnupg lsb-release
Output will look similar to:Install prerequisites

Make a directory for Docker's GPG key:

mkdir /etc/apt/demokeyrings
Use curl to download Docker's keyring and pipe it into gpg to create a GPG file so apt trusts Docker's repo:

 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/demokeyrings/demodocker.gpg
 
Add the Docker repo to your system with this command:

 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/demokeyrings/demodocker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
The output should look similar to:Add official Docker repo

#Step 2: Install Docker Compose And Related Packages
Now that you added Docker's repo, update your package lists again:

apt update -y
Next, install Docker-CE (Community Edition), the Docker-CE CLI, the containerd runtime, and Docker Compose with this command:

apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
Output should look similar to:Install Docker

You can verify Docker-CE, the Docker-CE CLI, containerd, and Docker Compose are installed by checking their versions with these commands:

docker --version; docker compose version;ctr version







Apache Nifi comes to mind if you are looking for a simple, but robust, tool to process data from various sources. 
In short, Apache NiFi is a tool to process and distribute data. Its intuitive UI supports routing definitions, a variety of connectors 
(in/out), and many built-in processors. All these features combined together make it a suitable optional platform for our use case.

#how to run nifi on ec2
https://hub.docker.com/r/apache/nifi/


https://hub.docker.com/r/apache/nifi-...

Step -1: Pull docker Image

docker pull apache/nifi:latest

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-08-23.png"/>

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

