# 08 - Spring Cloud Gatewayの構築

__This guide is part of the [Azure Spring Cloud training](../README.md)__

Build a [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway) to route HTTP requests to the correct Spring Boot microservices.

---

## Create a Spring Cloud Gateway

The application that we create in this guide is [available here](gateway/).

To create our gateway, we will use [https://start.spring.io/](https://start.spring.io/) with the command line:

```bash
curl https://start.spring.io/starter.tgz -d dependencies=cloud-gateway,cloud-eureka,cloud-config-client -d baseDir=gateway | tar -xzvf -
```

> We use the `Cloud Gateway`, `Eureka Discovery Client` and the `Config Client` components.

## Add a "cloud" Maven profile

*To deploy to Azure Spring Cloud, we add a "cloud" Maven profile like in the guide [05 - Build a Spring Boot microservice using Spring Cloud features](../05-build-a-spring-boot-microservice-using-spring-cloud-features/README.md)*

At the end of the application's `pom.xml` file (just before the closing `</project>` XML node), add the following code:

```xml
    <profiles>
        <profile>
            <id>cloud</id>
            <repositories>
                <repository>
                    <id>nexus-snapshots</id>
                    <url>https://oss.sonatype.org/content/repositories/snapshots/</url>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </repository>
            </repositories>
            <dependencies>
                <dependency>
                    <groupId>com.microsoft.azure</groupId>
                    <artifactId>spring-cloud-starter-azure-spring-cloud-client</artifactId>
                    <version>2.1.0-SNAPSHOT</version>
                </dependency>
            </dependencies>
        </profile>
    </profiles>
```

## Configure the application

Rename `src/main/resources/application.properties` to `src/main/resources/application.yml`, and add the following configuration:

```yaml
spring:
  cloud:
    gateway:
      discovery:
        locator:
          enabled: true
      globalcors:
        corsConfigurations:
          '[/**]':
            allowedOrigins: "*"
            allowedMethods:
              - GET

```

- The `spring.cloud.gateway.discovery.locator.enabled=true` part is to configure Spring Cloud Gateway to use the Spring Cloud Service Registry to discover the available microservices.
- The `spring.cloud.gateway.globalcors.corsConfiguration` part is to allow CORS requests to our gateway. This will be helpful in the next guide, when we will add a front-end that is not hosted on Azure Spring Cloud.

## Create the application on Azure Spring Cloud

As in [02 - Build a simple Spring Boot microservice](../02-build-a-simple-spring-boot-microservice/README.md), create a specific `gateway` application in your Azure Spring Cloud cluster. As this application is a gateway, we add the `--is-public true` flag so it is exposed publicly.

```bash
az spring-cloud app create -n gateway --is-public true
```

## Deploy the application

You can now build your "gateway" project and send it to Azure Spring Cloud:

```bash
./mvnw package -DskipTests -Pcloud
az spring-cloud app deploy -n gateway --jar-path target/demo-0.0.1-SNAPSHOT.jar
```

## Test the project in the cloud

- Go to "App Management" in your Azure Spring Cloud cluster.
  - Verify that `gateway` has a `Discovery status` which says `UP(1),DOWN(0)`. This shows that it is correctly registered in the Spring Cloud Service Registry.
  - Select `gateway` to have more information on the microservice.
- Copy/paste the public URL that is provided (there is a "Test Endpoint" like for microservices, but the gateway is directly exposed on the Internet, so let's use this).

As the gateway is connected to the Spring Cloud Service Registry, it should have automatically opened routes to the available microservices, with URL paths in the form of `/MICROSERVICE-ID/**`:

- Test the `city-service` microservice endpoint by doing: `curl https://XXXXXXXX.azureapps.io/CITY-SERVICE/cities` (replacing XXXXXXXX by the name of your gateway)
- Test the `weather-service` microservice endpoint by doing: `curl 'https://XXXXXXXX.azureapps.io/WEATHER-SERVICE/weather/city?name=Paris%2C%20France'` (replacing XXXXXXXX by the name of your gateway)

If you need to check your code, the final project is available in the ["gateway" folder](gateway/).

---

⬅️ Previous guide: [07 - Build a Spring Boot microservice using MySQL](../07-build-a-spring-boot-microservice-using-mysql/README.md)

➡️ Next guide: [09 - Putting it all together, a complete microservice stack](../09-putting-it-all-together-a-complete-microservice-stack/README.md)
