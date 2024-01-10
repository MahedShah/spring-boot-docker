# spring-boot-docker
first create a spring boot file from https://start.spring.io/
with maven and spring web


second step build a simple rest API 

@SpringBootApplication
@RestController
public class SpringBootDockerApplication {

	@GetMapping("/hello")
	public String hello(){
		return "any message";
	}

	public static void main(String[] args) {
		SpringApplication.run(SpringBootDockerApplication.class, args);
	}

}



then create a jar file from maven by using mvn package
after the jar file is created, ceate a new file in the root directory named as "Dockerfile"
and then type the following commands in the Dockerfile

FROM openjdk:17
VOLUME /tmp
ADD target/file.jar app.jar      #replace file.jar with your jar file name and app.jar with your application-name.jar 
ENTRYPOINT ["java", "-jar", "/app.jar"]

now building a docker image using command
docker build -t your-app:latest .   #replace your-app  with application name
now type 
docker images        # to make sure that the is created


to run docker image in a container type  docker run 8081:8080 your-app-name


