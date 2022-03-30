#  **<span style="color:green">Landmark Technologies, Ontario, Canada.</span>**
### **<span style="color:green">Contacts: +1437 215 2483<br> WebSite : <http://mylandmarktech.com/></span>**
### **Email: mylandmarktech@gmail.com**



## Apache Tomcat Installation And Setup In AWS EC2 Redhat Instnace.
##### Prerequisite
+ AWS Acccount.
+ Create Redhat EC2 T2.micro Instnace.
+ Create Security Group and open Tomcat ports or Required ports.
   + 8080 ..etc
+ Attach Security Group to EC2 Instance.
+ Install java openJDK 1.8+

### Install Java JDK 1.8+ & Tomcat version 9.0.55

``` sh
# install Java JDK 1.8+ as a pre-requisit for tomcat to run.
# vi tomcat.sh
cd /opt 
sudo yum install git wget -y
sudo yum install java-1.8.0-openjdk-devel -y
# Download tomcat software and extract it.
sudo yum install wget unzip -y
sudo wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.60/bin/apache-tomcat-9.0.60.tar.gz
sudo tar -xvf apache-tomcat-9.0.60.tar.gz
sudo rm apache-tomcat-9.0.60.tar.gz
sudo mv apache-tomcat-9.0.60 tomcat9
sudo chmod 777 -R /opt/tomcat9
sudo sh /opt/tomcat9/bin/startup.sh
# create a soft link to start and stop tomcat
sudo ln -s /opt/tomcat9/bin/startup.sh /usr/bin/starttomcat
sudo ln -s /opt/tomcat9/bin/shutdown.sh /usr/bin/stoptomcat
starttomcat
# tomcat configuration for the website
# vi /opt/tomcat9/webapps/manager/META-INF/context.xml
# add <!-- before the (<value className=) line and --> after the (allow) line
# to add user to the tomcat website 
# vi /opt/tomcat9/conf/tomcat-users.xml
# add the following after --> (under the second 2 the last line) right before </tomcat-users>
# <user username="alabaweh" password="admin" roles="manager-gui"/>
# <user username="admin" password="admin" roles="manager-script"/>
# exit and save


```

