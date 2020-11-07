# Spring Boot

### Why?
* easier to get started.
* minimize amount of manual configuration.
* resolve dependencies conflicts (maven or gradle).

**Spring Intializr**: https://start.spring.io/

### Dependencies:

1. **Spring Web**: Web App, Spring MVC, JSON, RESTful, Apache Tomcat, Hibernate Validator

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

2. **Spring Boot DevTools**: Fast application restarts, LiveReload

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
        </dependency>

3. **Spring Boot Actuator**: expose endpoints to monitor and manage your application

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>

    URL                  | Description
    ---------------------|------------------------------------
    /actuator/health     | Health info. about your application
    /actuator/info       | Info. about your application
    /actuator/mappings   | endpoints
    /actuator/beans      | 
    /actuator/threaddump | 

    * **application.properties**

                #expose everything
                management.endpoints.web.exposure.include=*

                #anything under info. will be monitor at /actuator/info
                info.app.name=My Project
                info.app.description=......
                info.app.version=1.0.0

4. **Spring Security**

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>

    * "user" with password generated in console (changed each run).
    * only accessible urls are /actuator/health & /actuator/info
    * customizing spring security: database roles, encrypt password -> follow regular spring security.
    * **application.properties**

                #hide /actuator/health & /actuator/info
                management.endpoints.web.exposure.exclude=health,info
                
                #override default user
                spring.security.user.name=ahmed
                spring.security.user.password=123
















