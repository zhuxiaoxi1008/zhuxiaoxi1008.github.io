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

# vscode 运行springboot 项目
```
run for java
maven for java

setting.json 文件增加

"java.configuration.maven.userSettings": "D:\\apache\\apache-maven-3.6.1\\conf\\settings.xml",
    "java.configuration.maven.globalSettings": "D:\\apache\\apache-maven-3.6.1\\conf\\settings.xml",
    "java.configuration.maven.localRepository": "D:\\apache\\localRepository",
    "maven.executable.path": "D:\\apache\\apache-maven-3.6.1\\bin\\mvn.cmd",
    "maven.terminal.customEnv": [
        {
          "environmentVariable": "JAVA_HOME",
          "value": "D:\\Program Files\\Java\\jdk1.8.0_51"
        }
      ],
    "maven.excludedFolders": [
        "**/.*",
        "**/node_modules",
        "**/target",
        "**/bin",
        "**/archetype-resources"
    ],


下载包 mvn clean install
编译   mvn clean compile
运行
```

# 设计模式

> 设计模式网站 https://refactoring.guru/design-patterns/singleton

