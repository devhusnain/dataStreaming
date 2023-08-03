# dataStreaming

#how to run nifi on ec2
https://hub.docker.com/r/apache/nifi/
https://hub.docker.com/r/apache/nifi-...

Step -1: Pull docker Image

docker pull apache/nifi:latest

<img src="https://raw.githubusercontent.com/devhusnain/dataStreaming/main/images/Screenshot%20from%202023-08-04%2001-08-23.png?token=GHSAT0AAAAAACF4RWEKR2RUVJMGXJVVLVNKZGMDGYQ"/>

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


