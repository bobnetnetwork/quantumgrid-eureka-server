
# Eureka Server

The **Eureka Server** is a microservice responsible for service discovery within the QuantumGrid platform. It acts as a service registry, allowing all microservices to register themselves and discover other services dynamically.

## Features

- Service registration and discovery
- Health checks for registered services
- High availability and scalability
- Integration with Spring Cloud for seamless microservice communication

## Technology Stack

- **Java**: Programming language
- **Spring Boot**: Framework for building the microservice
- **Spring Cloud Netflix Eureka**: Service registry and discovery server

## Getting Started

### Prerequisites

- **Java 17** or higher
- **Maven** for build automation

### Setup

1. **Clone the repository:**

    ```bash
    git clone https://github.com/bobnetnetwork/quantumgrid-eureka-server.git
    cd quantumgrid-eureka-server
    ```

2. **Configure Eureka Server properties:**

   Update the `src/main/resources/application.yml` file with the Eureka Server configuration:

    ```yaml
    server:
      port: 8761

    eureka:
      instance:
        hostname: localhost
      client:
        register-with-eureka: false
        fetch-registry: false
      server:
        enable-self-preservation: true
    ```

3. **Build the application:**

    ```bash
    mvn clean install
    ```

4. **Run the application:**

    ```bash
    mvn spring-boot:run
    ```

5. **Access the Eureka Dashboard:**

   Once the server is running, you can access the Eureka Dashboard at:
   
   ```
   http://localhost:8761
   ```

### Registering Microservices

To register other microservices with Eureka, add the following dependency to their `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
```

And configure the Eureka client settings in their `application.yml`:

```yaml
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/
  instance:
    prefer-ip-address: true
```

### Contributing

Please read the [CONTRIBUTING.md](https://github.com/bobnetnetwork/quantumgrid/blob/main/CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

### License

This project is licensed under the GPL-3.0 license - see the [LICENSE.md](https://github.com/bobnetnetwork/quantumgrid/blob/main/LICENSE.md) file for details.
