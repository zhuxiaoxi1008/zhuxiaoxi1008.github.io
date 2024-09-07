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


# 单例设计模式（Singleton Pattern）

## 概述
单例设计模式是一种常用的软件设计模式，它确保一个类只有一个实例，并提供一个全局访问点来获取这个实例。单例模式通常用于管理共享资源，如数据库连接、配置设置、日志记录器等。

## 特点
1. **唯一性**：单例类在应用程序的生命周期内只创建一个实例。
2. **全局访问点**：提供了一个全局访问点来获取实例。
3. **延迟初始化**：实例通常在第一次被引用时创建，而不是在程序启动时。

## 实现方式
单例模式有多种实现方式，以下是几种常见的实现方法：

### 1. 饿汉式（Eager Initialization）
在类加载时就立即初始化单例实例。
```java
public class Singleton {
    private static final Singleton INSTANCE = new Singleton();

    private Singleton() {}

    public static Singleton getInstance() {
        return INSTANCE;
    }
}
```

### 2. 懒汉式（Lazy Initialization）
只有在第一次被引用时才初始化实例。
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### 3. 双重检查锁定（Double-Check Locking）
减少同步的开销，只有在实例为 null 时才进行同步。
```java
public class Singleton {
    private static volatile Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

### 4. 静态内部类（Static Nested Class）
利用类加载机制保证初始化实例时只有一个线程。
```java
public class Singleton {
    private Singleton() {}

    private static class SingletonHolder {
        private static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```

### 5. 枚举（Enum）
使用枚举实现单例模式，具有序列化机制和反射攻击的防护。
```java
public enum Singleton {
    INSTANCE;

    public void doSomething() {
        // ...
    }
}
```

## 应用场景
- 需要严格控制资源使用的场景，如数据库连接池。
- 需要频繁访问、共享资源的场景，如配置信息、日志记录器。

## 优缺点
### 优点
- **控制资源消耗**：由于单例模式限制了实例的数量，可以有效地减少系统资源的消耗。
- **统一访问点**：提供了一个统一的访问点，便于管理和维护。

### 缺点
- **缺乏扩展性**：单例类的职责过重，难以扩展。
- **全局状态**：单例类持有全局状态，可能导致代码的耦合度增加。

## 注意事项
- 确保单例的线程安全。
- 考虑单例的序列化和反序列化问题。
- 避免在单例类中持有过多的状态，以免造成内存泄漏。

## 总结
单例设计模式是一种简单而强大的设计模式，它通过限制实例的数量来控制资源的使用，并提供一个全局访问点。在实现时，需要考虑线程安全、序列化安全以及如何在不牺牲性能的前提下实现懒加载。
