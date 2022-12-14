# Spring Boot Admin 

### [codecentric.github.io](https://codecentric.github.io/spring-boot-admin/2.7.3/)

## O que é o Spring Boot Admin?

O Spring Boot Admin da codecentric é um projeto comunitário para gerenciar e monitorar seus aplicativos Spring Boot ®. Os aplicativos se registram em nosso Spring Boot Admin Client (via HTTP) ou são descobertos usando Spring Cloud ® (por exemplo, Eureka, Consul). A interface do usuário é apenas um aplicativo Vue.js sobre os endpoints do Spring Boot Actuator.

## Configurando o Spring Boot Admin Server

Primeiro, você precisa configurar seu servidor. Para fazer isso, basta configurar um projeto de inicialização simples (usando start.spring.io). Como o Spring Boot Admin Server é capaz de ser executado como servlet ou aplicativo webflux, você precisa decidir sobre isso e adicionar o Spring Boot Starter correspondente. Neste exemplo, estamos usando o servlet web starter.

1. Adicione o iniciador do Spring Boot Admin Server às suas dependências:
```xml
<dependency>
  <groupId>de.codecentric</groupId>
  <artifactId>spring-boot-admin-starter-server</artifactId>     
  <version>2.7.3</version>
</dependency>
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
2. Puxe a configuração do Spring Boot Admin Server adicionando @EnableAdminServer à sua configuração:
```java
@Configuration  
@EnableAutoConfiguration  
@EnableAdminServer  
public  class  SpringBootAdminApplication { 
  public  static  void main(String[] args) {
     SpringApplication.run(SpringBootAdminApplication.class, args); 
  }
}
```

## Registrando aplicativos cliente
Para registrar seu aplicativo no SBA Server, você pode incluir o SBA Client ou usar o Spring Cloud Discovery (por exemplo, Eureka, Consul, …​). Há também uma opção simples usando uma configuração estática no lado do servidor SBA.

1. Adicione spring-boot-admin-starter-client às suas dependências:
```xml
<dependency>
   <groupId>de.codecentric</groupId>
   <artifactId>spring-boot-admin-starter-client</artifactId>
   <version>2.7.4</version>
</dependency>
```

2. Habilite o SBA Client configurando a URL do Spring Boot Admin Server:
```properties
spring.boot.admin.client.url=http://localhost:8080  
management.endpoints.web.exposure.include=*  
management.info.env.enabled=true 
```
