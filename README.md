# oxAuth-rp-spring-boot-quickstart-demo

This project is an application skeleton for oxAuth using Java and Spring Boot to quickly bootstrap your oxAuth projects.

It's a pre-configured Maven project containing a sample oxAuth authentication and all required dependencies.

The sample application is a Spring Boot RP of [Gluu Server 4.1][1].
For information on how to setup your Gluu Server you can follow along with the [Installation Guide][2].


## Prerequisites
* Git
* JDK 6 or later
* Maven 3.0 or later
* Tomcat 6.x or later

### Create Client in Gluu Server Admin UI

Navigate to OpenID Connect > Client and Click Add Client Button

Sample Config in creating a Client:
```
* client name: Spring Boot Demo
* response type: code
* grant type: authorization_code
* Redirect Login URIs: http://localhost:8080/login/oauth2/code/oxauth
* Redirect Logout URIs: http://localhost:8080
* Pre-authorization: true
* Scopes: openid, email, profile
* subject type: public
```

### Add Gluu Server IP and Hostname to host file

Edit the hosts file and add your Gluu Server IP Address and hostname. For example:
```
192.168.1.1 test.gluu.org
```
The Windows hosts file is located at C:\Windows\System32\drivers\etc\hosts

### Import Your Gluu Server Host certificate
You can download your Gluu Server certificate in Configuration > Certicates. Download the HTTPD SSL certificate.

Then import the GLuu Server certifcate to your JVM with the follwing command:
```
keytool -importcert -file gluucert.cer -alias gluucert -keystore “%JAVA_HOME%/jre/lib/security/cacerts”
```
Restart your machine/device.

## Getting Started

### Clone
To get started you can simply clone this repository using git:
```
git clone https://github.com/GluuFederation/spring-boot-demo.git
cd spring-boot-demo
```
Or if you have GitHub Desktop application, You can clone the repository by navigating to File > Clone Repository > URL Tab and enter the repository url:
```
https://github.com/GluuFederation/spring-boot-demo.git
```

### Configuration
In order to get your app working you have to provide the following settings:
```
issuer-uri = your.gluu.server.hostname
client-id = your-app-client-id
client-secret = your-app-client-secret
```
The configuration is located in `\src\main\resources\application.yml`.

### Running the application locally

There are several ways to run a Spring Boot application on your local machine. One way is to execute the `main` method in the `org.gluu.demo.RpSpringBootApplication` class from your IDE.

Alternatively you can use the [Spring Boot Maven plugin](https://docs.spring.io/spring-boot/docs/current/reference/html/build-tool-plugins-maven-plugin.html) like so:
```shell
mvn spring-boot:run
```
*Instead of `mvn` you can also use the maven-wrapper `./mvnw` to ensure you have everything necessary to run the Maven build.*
```shell
mvnw spring-boot:run
```
In order to run the maven command, navigate first to your cloned spring-boot-demo directory.

### Test Run the RP spring boot app
You can test the application by going to your browser and enter:
```
http://localhost:8080/
```

### Deploy the app to Tomcat Server
In your IDE. Add the rp-spring-boot project to your Tomcat Server.
Restart your tomcat server and go to your browser and enter:
```
http://localhost:8080/rp-spring-boot/
```




[1]: https://gluu.org/docs/gluu-server/
[2]: https://gluu.org/docs/gluu-server/4.1/installation-guide/
