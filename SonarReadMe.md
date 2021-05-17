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

