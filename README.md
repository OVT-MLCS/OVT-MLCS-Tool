# Installation & Deployment
## 1. Prerequisites
**OVT-MLCS** is a lightweight Web application, and has implemented using `JDK 21`. Before deployment of OVT-MLCS, Your Web server should meet that 1) Java JDK 21 has already installed, and 2) RAM ≥ 32GB for MLCS mining tasks from big sequences (length ≥ 10,000). Otherwise, please follow the instructions below to install `JDK 21`. It is noting that you can download the latest version of JDK from the [Oracle website](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html) or use a package manager like `apt` or `yum` for Linux system.

```shell
# Linux/macOS  
# 1. Visit Oracle JDK 21 download page:  
#    https://www.oracle.com/java/technologies/downloads/#jdk21-linux  
# 2. Download the .rpm/.tar.gz package for your OS  
# 3. Extract and move to /usr/lib/jvm  
# Example (Linux):  
sudo mkdir -p /usr/lib/jvm  
sudo tar -xzf jdk-21_linux-x64_bin.tar.gz -C /usr/lib/jvm  
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-21/bin/java 2100  
```

## 2. Installation
Excute the following commands in a Linux shell to install the OVT-MLCS, which would cost about several minutes to finish the installation.

```shell
unzip OVT-MLCS-APP.zip
cd OVT-MLCS-APP
bin/init.sh
```

When executing `bin/init.sh`, it will automatically download and install related components including **AntX6**, **Bootstrap HTML**, **Beangle Web**, and the **H2 database** for OVT-MLCS. Please ensure your network connection is stable before running the script to allow `bin/init.sh` to complete successfully.


## 3. Run the Web Application
To run the OVT-MLCS, please execute the following command in the Linux shell. 

```shell
bin/start.sh mlcs
```

## 4. Stop the Web Application
To stop the OVT-MLCS, please execute the following command in the Linux shell. 

```shell
bin/stop.sh mlcs
```
## 5. Configuration
By editing the configuration file `conf/server.xml`, you can change the memory and port settings of your Web server's runtime environment.

```xml
<Farm name="mlcs" engine="tomcat11" maxHeapSize="500m">
  ...
  <Server name="server1"  http="6980"  />
</Farm>
```

`maxHeapSize` specifies the maximum heap size for the Java Virtual Machine (JVM). You can change it to `32G` or more based on your system's memory capacity.

`http="6980"` specifies the HTTP port for the web application. You can change it to `8080` or any other available port.




















