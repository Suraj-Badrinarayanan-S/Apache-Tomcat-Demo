# Apache-Tomcat-Demo
This project demonstrates the installation, configuration, and deployment of a Java-based web application on Apache Tomcat 9. 

The step-by-step guide outlines how to set up the Tomcat server, configure user access, and deploy a sample WAR (Web Application Archive) file to showcase the deployment process.

# Steps to Run
Start Tomcat:


sudo startTomcat

Access the Tomcat Manager:

URL: http://<server-ip>:8080/manager
Login using the credentials defined in tomcat-users.xml (e.g., admin/admin1234).

View the Deployed Application:

Place the .war file in the webapps folder.
Access the application at http:// <server-ip>:8080/petclinic.

Stop Tomcat (if needed):

sudo stopTomcat

# We can now use the webpage at localhost:8080/petclinic

![image](https://github.com/user-attachments/assets/0209c1ff-cfd9-425a-b28c-fd282f06dd1f)
