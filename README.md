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
##### Extraiga la configuración del servidor de administración de Spring Boot agregando @EnableAdminServera su configuración:
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

