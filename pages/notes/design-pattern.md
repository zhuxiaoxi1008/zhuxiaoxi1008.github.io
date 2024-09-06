# spring start
> https://start.spring.io/

# idea 热部署
```
    1.Fiel->settings->Build,Execution,Deployment->Compiler
    勾选 Build project automatically

    2 CTRL + SHIFT + A --> 查找Registry
    勾选  compiler.automake.allow.when.app.running

    3 pom.xml加入springboot开发者包

    <!-- springboot热部署工具 -->
    <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <optional>true</optional>
    </dependency>
    4 开启springboot热部署
    <!--开启springboot热部署 该配置必须-->
    <plugins>
    <plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
        <configuration>
        <fork>true</fork>
        </configuration>
    </plugin>
    </plugins>
    即可完成springboot热部署
```

# 设计模式

> 设计模式网站 https://refactoring.guru/design-patterns/singleton

