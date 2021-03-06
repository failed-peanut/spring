# Traditional, *very Traditional* way of writing Spring Web Application.
[complete code: spring-boot-web-application](https://github.com/failedpeanut/spring/tree/main/spring-boot-web-application)

### Modules Used
* Spring Boot: 2.5.1
* Spring Web
* Spring Data JPA
* H2 Database
* JSP support for Web UI
* embedded tomcat
* Refer [pom.xml](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/pom.xml) for complete details.

### Set up
* Create Spring Boot Starter Application.

* Select Modules:

	1. Spring Boot DevTools (*helps in development process*)
	
	2. Spring Data JPA
	
	3. H2 Database
	
	4. Spring Web
	
* Add below additional dependencies:
		
		<dependency>
			<groupId>org.apache.tomcat.embed</groupId>
			<artifactId>tomcat-embed-jasper</artifactId>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jstl</artifactId>
			<scope>provided</scope>
		</dependency>
		
		

* `spring-boot-starter-web` includes the `spring-boot-starter-tomcat`

* `spring-boot-starter-tomcat` includes the `tomcat-embed-core`

* `tomcat-embed-core` doesn't include `tomcat-embed-jasper`. In fact, is `tomcat-embed-jasper` who includes dependency with `tomcat-embed-core`.

* `tomcat-embed-jasper` is marked as provided, so indicates that you expect the JDK or a container to provide the dependency at runtime. 

* This scope is only available on the compilation and test classpath, and is not transitive.

* the `spring-boot-starter-web` includes the tomcat embedded dependency but it doesn't includes the jasper embedded dependency, so that should be the reason to declare it separately.

### Classes
* [SpringBootWebApplication.java](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/java/com/failedpeanut/springboot/webapplication/SpringBootWebApplication.java)

	The Main class from where application starts.

* [UserController.java](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/java/com/failedpeanut/springboot/webapplication/UserController.java)

	The controller class which receives HTTP requests and renders views.

* [UserRepository.java](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/java/com/failedpeanut/springboot/webapplication/UserRepository.java)

	A JPA Repository which queries Database.

* [UserService.java](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/java/com/failedpeanut/springboot/webapplication/UserService.java)

	A service class which communicate with Repository to access database and send data to controller.

* [UserEntity.java](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/java/com/failedpeanut/springboot/webapplication/UserEntity.java)

	A Entity object for user table. It acts as DAO and DTO.

* [users.jsp](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/webapp/WEB-INF/jsp/users.jsp)

	The jsp view which uses JSTL tags and sends and gets data from controller.
	
### Starting Application

	http://localhost:8081/users

### H2 Database console (*can be accessed once application starts*)
	*username and password check in below file* 
[application.properties](https://github.com/failedpeanut/spring/blob/main/spring-boot-web-application/src/main/resources/application.properties)

	H2 console URL- http://localhost:8081/h2-console
	