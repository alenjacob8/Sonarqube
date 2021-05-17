<h1>SonarQube Installation on EC2</h1>
<h2>Prerequisites</h2>
<h3>Minimum hardware requirements:</h3>

- A small-scale (individual or small team) instance of the SonarQube server requires at least 2GB of RAM to run efficiently and 1GB of free RAM for the OS. If you are installing an instance for a large teams or Enterprise, please consider the additional recommendations below.

 - The amount of disk space you need will depend on how much code you analyze with SonarQube.

- SonarQube must be installed on hard drives that have excellent read & write performance. Most importantly, the "data" folder houses the Elasticsearch indices on which a huge amount of I/O will be done when the server is up and running. Great read & write hard drive performance will therefore have a great impact on the overall SonarQube server performance.

- SonarQube does not support 32-bit systems on the server side. SonarQube does, however, support 32-bit systems on the scanner side.

<h2>Installing SonarQube in AWS Instance</h2>
<h3>InstanceTye</h3>

- Instance Type: t3a.medium or t3.medium

- SonarQube scanners require version 8 or 11 of the JVM and the SonarQube server requires version 11. Versions beyond Java 11 are not officially supported.
- For more details, refer https://docs.sonarqube.org/latest/requirements/requirements/

<h2>Installation Guide</h2>

- After configuring your EC2 server in cloud, connect to the Server using the Putty or any terminal

<b><i>Note: </i></b>

- If you do not have a key pair configured, then you need to create a new key pair, download the same and use Puttygen to generate the private key
- Once private key is configured you can use the private key to connect to ec2 instance  using the public IP address

For more details, refer AWS Documentation for https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html

<h2>Configuration of EC2 Server</h2>

- After connecting to EC2 using SSH, lets configure the server with prerequisities

We need install:

- JDK11
- JRE11
- Docker

- Elevate as Root User

<code>sudo su</code>

- Get docker-compose

<code>sudo wget https://raw.githubusercontent.com/duorg/Scripts/master/docker-compose.yml</code></br>
<code>sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose</code></br>
<code>sudo chmod +x /usr/local/bin/docker-compose</code></br>

- Check the docker-compose version

<code>sudo docker-compose version</code>

- Create two files Dockerfile, sonar.properties with the below content

File1:Dockerfile
--------------------------------------
FROM sonarqube:7.9-community</br>
COPY sonar.properties /opt/sonarqube/conf/

File2: sonar.properties
----------------------------------------
sonar.junit.reportPaths=target/surefire-reports</br>
sonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml

#Creating the files
----------------------------------------
sudo vi Dockerfile<br>
FROM sonarqube:7.9-community<br>
COPY sonar.properties /opt/sonarqube/conf/<br>

sudo vi sonar.properties</br>
sonar.junit.reportPaths=target/surefire-reports</br>
sonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml</br>



- Change the directory back to root

  <code> cd ..</code>

<h2>Configuration of SonarQube Server</h2>

<h3>Preparing the environment</h3>

<b>In order the run SonarQube in Ubuntu, you must ensure that</b>

- vm.max_map_count is greater than or equal to 524288
- fs.file-max is greater than or equal to 131072
- the user running SonarQube can open at least 131072 file descriptors
- the user running SonarQube can open at least 8192 threads

<b>You can see the values with the following commands:</b>

- sysctl vm.max_map_count
- sysctl fs.file-max
- ulimit -n
- ulimit -u






