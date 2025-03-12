### mybatis-spring-boot
https://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/zh_CN/index.html
https://www.w3cschool.cn/mybatis3/mybatis3-4vgu3nex.html
https://start.spring.io/

mybatis3
https://blog.csdn.net/weixin_43004044/article/details/120253014

## springboot整合mybatis

### pom.xml
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.demo</groupId>
	<artifactId>mybatis</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>mybatis</name>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.4.0</version>
	</parent>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>17</java.version>
	</properties>
	<dependencies>
		<!-- Spring Boot -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>


		<!-- Spring Boot MyBatis Starter -->
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis</artifactId>
			<version>3.5.17</version>
		</dependency>
		
		<dependency>
			<groupId>org.mybatis.spring.boot</groupId>
			<artifactId>mybatis-spring-boot-starter</artifactId>
			<version>3.0.4</version>
		</dependency>

		<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-spring-boot3-starter</artifactId>
			<version>3.5.9</version>
		</dependency>

		<!-- 数据库驱动，根据你的数据库选择相应的驱动 -->
		<dependency>
			<groupId>com.mysql</groupId>
			<artifactId>mysql-connector-j</artifactId>
			<version>8.0.33</version>
		</dependency>

		<!-- Lombok 依赖 -->
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<version>1.18.20</version>
		</dependency>

		<dependency>
			<groupId>jakarta.persistence</groupId>
			<artifactId>jakarta.persistence-api</artifactId>
			<version>3.1.0</version>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
			<optional>true</optional>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>
</project>
```
### application.yml
``` yaml
server:
  port: 8080
spring:
  datasource:
    url: jdbc:mysql://192.168.80.129:3306/mybatis
    username: root
    password: 123456
    driver-class-name: com.mysql.cj.jdbc.Driver
mybatis:
  mapper-locations: classpath:mapper/*.xml
  type-aliases-package: com.demo.mybatis.entity
```

### [mybatis-plus](https://baomidou.com/getting-started/)
https://baomidou.com/getting-started/

#### 处理类属性与数据库字段不一致
方法一：在实体类上使用`@TableField`注解，指定数据库字段名
``` java
package com.demo.mybatis.entity;

import com.baomidou.mybatisplus.annotation.TableField;
import com.baomidou.mybatisplus.annotation.TableName;
import lombok.Data;

@Data
@TableName("`user`")
public class User {
    private Long id;
    private String name;
    private Integer age;
    private String email;
    @TableField("class_name")
    private String className;
    private String bbb;
}
```
	方法二：在mapper.xml中，使用`<resultMap>`标签，指定数据库字段名和实体类属性名之间的映射关系
``` xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.demo.mybatis.mapper.AccountMapper">
    <resultMap id="Account" type="com.demo.mybatis.entity.Account">
        <result property="userName" column="user_name"/>
    </resultMap>

    <select id="selectUserById" resultMap="Account">
        SELECT * FROM tb_account WHERE id = #{id}
    </select>

    <select id="selectList" resultMap="Account">
        SELECT * from tb_account
    </select>
</mapper>
```
方法三：开启驼峰命名转换
在`application.yml`中，使用`mybatis-plus: configuration: map-underscore-to-camel-case: true`，开启驼峰命名转换
mybatis：
  configuration:
    map-underscore-to-camel-case: true
