# Spring boot Admin

### Pre-requisitos 📋
* _Debe tener instalado el actuator, ya que el Spring Boot Admin leera informacion que expone esa libreria_

### Instalación 🔧

##### Agregue el iniciador Spring Boot Admin Server a sus dependencias:
```
<dependency>
    <groupId>de.codecentric</groupId>
    <artifactId>spring-boot-admin-starter-server</artifactId>
    <version>2.1.6</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
##### Extraiga la configuración del servidor de administración de Spring Boot agregando ```@EnableAdminServer``` a su configuración:
```
@Configuration
@EnableAutoConfiguration
@EnableAdminServer
public class SpringBootAdminApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringBootAdminApplication.class, args);
    }
}
```
* _En este punto Spring Boot Admin ya estaria funcionando con la informacion basica._
* _Puede consultar en el localhost:[Puerto definido]//#admin y te redicrecciona a la pagina del spring boot admin._

### Configuraciones Adicionales 🔧
##### Esta configuracion activa todas las pestañas, a menos de que configure las que quiera que salgan ```eje: include: auditevents,info ```
```
management:
  endpoints:
    web:
      exposure:
        include: "*" #auditevents,info,health,metrics,configprops,logfile,shutdown,mappings,threaddump
```
```
info:
  app:
    name: NOMBRE-APP
    description: Demo project for Spring Boot
    version: 0.0.1-SNAPSHOT
    port: ${local.server.port}
    PID: ${PID}
  java:
    vendor: ${java.vm.vendor}
    version: ${java.version}
  user:
    name: ${user.name}
    timezone: ${user.timezone}
    country: ${user.country}
```
### Configuraciones para ver las otras api 🔧

##### Agregue el iniciador Spring Boot Admin Server a sus dependencias:
```
<dependency>
    <groupId>de.codecentric</groupId>
    <artifactId>spring-boot-admin-starter-server</artifactId>
    <version>2.1.6</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
##### Extraiga la configuración del servidor de administración de Spring Boot agregando ```@EnableAdminServer``` a su configuración:
```
@Configuration
@EnableAutoConfiguration
@EnableAdminServer
public class SpringBootAdminApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringBootAdminApplication.class, args);
    }
}
```
##### Agregar al yml las url donde estan montados las demas api
```
cloud:
    discovery:
      client:
        simple:
          instances:
            api1:
              - uri: http://localhost:20006/
                metadata:
                  management.context-path: /actuator
            api2:
              - uri: http://localhost:20004/
                metadata:
                  management.context-path: /actuator
            api3:
              - uri: http://localhost:20003/
                metadata:
                  management.context-path: /actuator
            api4:
              - uri: http://localhost:20008/
                metadata:
                  management.context-path: /actuator

```
* _Asi podremos ver informacion de todas las api con tan solo un par de clicks._

## Versionado 📌
codecentric - [url](https://mvnrepository.com/artifact/de.codecentric/spring-boot-admin-starter-server)
## Fuente ✒️
codecentric - [url](https://codecentric.github.io/spring-boot-admin/2.1.6/#_other_discoveryclients)
