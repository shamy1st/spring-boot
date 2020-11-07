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

5. **Spring Data JPA**: JPA, Hibernate, Spring Data JPA

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

    * automatically get these methods: findAll(), findById(), save(), deleteById()
    * you can add custom queries with JPQL
    * Query Domain Specific Language (Query DSL)

            public interface EmployeeRepository extends JpaRepository<Employee, Integer> {
                //no need to write any code
            }

6. **Database**

    * **MySQL Driver**

            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <scope>runtime</scope>
            </dependency>

    * **Oracle Driver**

            <dependency>
                <groupId>com.oracle.database.jdbc</groupId>
                <artifactId>ojdbc8</artifactId>
                <scope>runtime</scope>
            </dependency>

7. **Rest Repositories**: Spring Data REST

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-rest</artifactId>
        </dependency>

    * spring data rest will scan for JpaRepository
    * it will expose all CRUD endpoints by default.
    * the same name of Entity lowercase + "s" (Employee -> employees)

        --     | url                     | description
        -------|-------------------------|-----------------------------
        POST   | /employees              | create new employee
        GET    | /employess              | read a list of employees
        GET    | /employess/{employeeId} | read a single employee
        PUT    | /employess/{employeeId} | update an existing employee
        DELETE | /employess/{employeeId} | delete an existing employee

    * Spring Data REST are HATEOAS compliant
    * HATEOAS: Hypermedia As The Engine Of Application State.
    * customize url: example change "employees" to "members"

            @RepositoryRestResource(path="members")
            public interface EmployeeRepository extends JpaRepository<Employee, Integer> {
                
            }
    * customize path: in application.properties file

            spring.data.rest.basePath=/api
    
8. **Lombok**: reduce boilerplate code such as setters/getters

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>

    * in Entity class just add @Data and setters/getters will be generated automatically.
    
            @Entity
            @Data
            public class Employee {
                // fields

                // no need to generate setters/getters
            }







