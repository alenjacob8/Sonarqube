<h1>SonarQube Installation on EC2</h1>
<h2>Prerequisites</h2>
<h3>Minimum hardware requirements:</h3>
- A small-scale (individual or small team) instance of the SonarQube server requires at least 2GB of RAM to run efficiently and 1GB of free RAM for the OS. If you are installing an instance for a large teams or Enterprise, please consider the additional recommendations below.

 -The amount of disk space you need will depend on how much code you analyze with SonarQube.

- SonarQube must be installed on hard drives that have excellent read & write performance. Most importantly, the "data" folder houses the Elasticsearch indices on which a huge amount of I/O will be done when the server is up and running. Great read & write hard drive performance will therefore have a great impact on the overall SonarQube server performance.

- SonarQube does not support 32-bit systems on the server side. SonarQube does, however, support 32-bit systems on the scanner side.
