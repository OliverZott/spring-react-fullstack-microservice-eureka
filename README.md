# Prerequisites
## Setup JAVA_HOME and gradle
After installing java and gradle,
ADD

> export JAVA_HOME="/usr/bin/java"  
export PATH=$PATH:$JAVA_HOME/bin   
export PATH=$PATH:/opt/gradle/gradle-7.3.1/bin  

TO
- `sudo gedit /etc/profile` and
- `sudo gedit .bashrc`

**If ERRORS:**
- https://stackoverflow.com/questions/22307516/gradle-finds-wrong-java-home-even-though-its-correctly-set
- Make JAVA_HOME == dir above bin where javac lives as in

> type javac
> javac is /usr/bin/javac   # now check if its just a symlink
> ls -la /usr/bin/javac
> /usr/bin/javac -> /etc/alternatives/javac   # its a symlink so check again
> ls -la /etc/alternatives/javac  # now check if its just a symlink
> /etc/alternatives/javac -> /usr/lib/jvm/java-8-openjdk-amd64/bin/javac
> OK so finally found the bin above actual javac so do this

> export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64     
export PATH=$JAVA_HOME/bin:$PATH



------------------------------------------------------------
# Eureka Discovery Server

## Resources

- https://www.tutorialspoint.com/spring_boot/spring_boot_eureka_server.htm
- https://roytuts.com/use-of-eureka-server-in-microservices/
- https://spring.io/guides/gs/service-registration-and-discovery/

> The Eureka server is nothing but an implementation of **service discovery pattern**, where microservices can register themselves so others can discover them.

> This server holds information about the client service applications. Each microservice registers into Eureka server and eureka server knows all client applications running on each port and IP address. This server is also known as discovery server.

> The @EnableEurekaServer annotation is used to make your Spring Boot application acts as a Eureka Server.

> A service registry is useful because it enables client-side **load-balancing** and **decouples** service providers from consumers without the need for DNS.

- Run application and check `http://localhost:8761`



------------------------------------------------------------
# Create and run

- Run application in IDE and check http://localhost:8761

OR
- #### Prerequisite: 
  Create Gradle Wrapper for application:
  https://docs.gradle.org/current/userguide/gradle_wrapper.html
  - 
- Create and run **JAR**
  - `gradle clean build` or if maven: `mvn clean install`
  - `java –jar <JARFILE> ` (inside */build/libs* )