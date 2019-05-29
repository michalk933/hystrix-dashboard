How to add hystrix to project
====================

### 1.Add dependency
From spring boot 2.0.0 you must add actuator to project.
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-hystrix</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

### 2.Add annotation ahead run class.
```java
@EnableCircuitBreaker
```

### 3.Add annotation into rest controller method, which one you want monitoring
Set port, turn off registration for simple test.
```java
@HystrixCommand
```

### 4.OPTIONAL! If you want curiculumBreaker, add annotation with name method fallBack.
```java
@HystrixCommand(fallbackMethod = "getReservationNamesFallback")

public Collection<String> getReservationNamesFallback() {
   return new ArrayList<>();
}
```

### 5.Add posts to application.properties
```java
management.endpoints.web.exposure.include=*
```





How to add dashboard hystrix
====================

### 1.Add dependency
From spring boot 2.0.0 you must add actuator to project.
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-netflix-hystrix-dashboard</artifactId>
</dependency>
```

### 2.Add annotation ahead run class
```java
@EnableHystrixDashboard
```

### 3.Add posts to application.properties
Set port, turn off registration for simple test.
```java
management.endpoints.web.exposure.include=hystrix.stream
```
