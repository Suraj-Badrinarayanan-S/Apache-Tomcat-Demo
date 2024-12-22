# Commands to be used to setup server:

```bash
cd /opt
# Navigate to the /opt directory, typically used for optional or third-party software installations.

sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz
# Download the Apache Tomcat 9.0.65 binary archive from the official archive repository.

sudo tar -xvf apache-tomcat-9.0.65.tar.gz
# Extract the downloaded tar.gz file, which contains the Tomcat installation files.

cd /opt/apache-tomcat-9.0.65/conf
# Navigate to the 'conf' directory where Tomcat's configuration files are located.

sudo vi tomcat-users.xml
# Open the 'tomcat-users.xml' file in the vi editor to configure user access.

# ---add-below-line at the end (2nd-last line)----
# <user username="admin" password="admin1234" roles="admin-gui, manager-gui"/>
# Add a new admin user with roles to access the admin GUI and manager GUI of Tomcat.

sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
# Create a symbolic link for the 'startup.sh' script to allow starting Tomcat using the 'startTomcat' command.

sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat
# Create a symbolic link for the 'shutdown.sh' script to allow stopping Tomcat using the 'stopTomcat' command.

sudo vi /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml
# Open the 'context.xml' file of the manager application to modify its configuration.

# comment:
<!-- Valve className="org.apache.catalina.valves.RemoteAddrValve"
  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
# Comment out the RemoteAddrValve configuration to allow external access to the manager application.

sudo vi /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml
# Open the 'context.xml' file of the host-manager application to modify its configuration.

# comment:
<!-- Valve className="org.apache.catalina.valves.RemoteAddrValve"
  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
# Comment out the RemoteAddrValve configuration to allow external access to the host-manager application.

sudo stopTomcat
# Stop the Tomcat server using the 'stopTomcat' command (symbolic link to shutdown.sh).

sudo startTomcat
# Start the Tomcat server using the 'startTomcat' command (symbolic link to startup.sh).

sudo cp target/*.war /opt/apache-tomcat-9.0.65/webapps/
# Copy the compiled WAR file(s) from the target directory to Tomcat's 'webapps' directory for deployment.

