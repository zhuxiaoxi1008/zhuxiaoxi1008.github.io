## [mybatis 官网](https://mybatis.net.cn/getting-started.html)
### [mybatis plus 教程](https://www.baeldung.com/spring-boot-annotations)

^\s*$\n 空白行替换 点击 .*
### mybatis-spring-boot
https://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/zh_CN/index.html
https://www.w3cschool.cn/mybatis3/mybatis3-4vgu3nex.html
https://start.spring.io/
mybatis3
https://blog.csdn.net/weixin_43004044/article/details/120253014
## springboot 整合 mybatis
### 1.环境准备
pom.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.5.6</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.mybatis</groupId>
    <artifactId>test</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>test</name>
    <description>Demo project for Spring Boot</description>
    <properties>
        <java.version>17</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <!-- MyBatis Spring Boot Starter -->
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>3.0.3</version>
        </dependency>
        <!-- Lombok (optional) -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <excludes>
                        <exclude>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                        </exclude>
                    </excludes>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```
application.yml
```yml
spring:
  application:
    name: test
  datasource:
    url: jdbc:mysql://localhost:3306/mybatis
    username: root
    password: 123456
    driver-class-name: com.mysql.cj.jdbc.Driver
mybatis:
  mapper-locations: classpath:mapper/**/*Mapper.xml
  type-aliases-package: com.mybatis.test.entity
  configuration:
    map-underscore-to-camel-case: true
```
mapper.xml
``
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.mybatis.test.mapper.StudentMapper">
    <select id="selectStudent" resultType="Student">
        select * from student
    </select>
</mapper>
```
映射类 class
```java
package com.mybatis.test.mapper;
import com.mybatis.test.entity.Student;
import org.apache.ibatis.annotations.Mapper;
import java.util.List;
@Mapper
public interface StudentMapper {
    List<Student> selectStudent();
}
```
启动类
```java
package com.mybatis.test;
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
@SpringBootApplication
@MapperScan("com.mybatis.test.mapper")
public class TestApplication {
    public static void main(String[] args) {
        SpringApplication.run(TestApplication.class, args);
    }
}
```
### pom.xml
```xml
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
```yaml
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
## 2.CRUD
controller 
``` java
package com.mybatis.test.controller;
import com.mybatis.test.entity.Student;
import com.mybatis.test.mapper.StudentMapper;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;
import java.util.List;
@RestController
public class StudentController {
    @Autowired
    StudentMapper studentMapper;
    @GetMapping("/get")
    public List<Student> selectStudent(){
        return studentMapper.selectStudent();
    }
    @PostMapping("/add")
    public Boolean addStudent(@RequestBody Student student){
       return studentMapper.addStudent(student);
    }
    @PostMapping("/update")
    public Boolean updateStudent(@RequestBody Student student){
        return studentMapper.updateStudent(student);
    }
    @PostMapping("/delete/{id}")
    public Boolean deleteStudent(@PathVariable String id){
        System.out.println(id);
        return studentMapper.deleteStudent(id);
    }
}
```
mapper 
``` java
package com.mybatis.test.mapper;
import com.mybatis.test.entity.Student;
import org.apache.ibatis.annotations.Mapper;
import java.util.List;
@Mapper
public interface StudentMapper {
    List<Student> selectStudent();
    Boolean addStudent(Student student);
    Boolean updateStudent(Student s);
    Boolean deleteStudent(String id);
}
```
mapperxml
``` xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.mybatis.test.mapper.StudentMapper">
    <select id="selectStudent" resultType="Student">
        select * from student
    </select>
    <insert id="addStudent">
        insert into student (id,name,age)
        values (#{id},#{name},#{age})
    </insert>
    <update id="updateStudent">
        update student set name=#{name},age=#{age} where id=#{id}
    </update>
    <delete id="deleteStudent">
        delete from student where id=#{id}
    </delete>
</mapper>
```
test.rest
``` r
@baseUrl = http://localhost:8080
@contentType = application/json
###
// 一级部门
GET  {{baseUrl}}/get  HTTP/1.1
content-type: application/json
###
POST {{baseUrl}}/add  HTTP/1.1
content-type: application/json
{"id": "3", "name": "Tom", "age": 15}
###
POST {{baseUrl}}/update  HTTP/1.1
content-type: application/json
{"id": "3", "name": "Tom(update2)", "age": 18}
###
POST {{baseUrl}}/delete/4  HTTP/1.1
content-type: application/json
# {"id": "4"}
```
jackson 序列化策略
1.命名策略
spring.jackson.property-naming-strategy=SNAKE_CASE
2.Pojo 字段映射序列化反序列化设置 **推荐**
@JsonProperty("sId")
private int sId;
同一字段序列号两次 原因
Spring Boot中，默认的命名策略是 LOWER_CAMEL_CASE（即驼峰命名，首字母小写）
Lombok 会为字段 sId 生成 getter 和 setter
解决思路
```
@JsonProperty("sId")  // 在 getter 方法上明确指定  
public int getSId() {  
    return sId;  
}  
@JsonProperty("sId")  // 在 setter 方法上明确指定  
public void setSId(int sId) {  
    this.sId = sId;  
}
```
## 3.复杂查询
association 使用 
Pojo 中添加一个 student 属性 对应
一对一映射   使用 select 嵌套
``` xml
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE mapper  
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">  
<mapper namespace="com.mybatis.test.mapper.BlogMapper">  
    <resultMap id="BlogStudent" type="Blog">  
        <result property="id" column="id"/>  
        <result property="title" column="title"/>  
        <result property="sId" column="s_id"/>  
        <association property="student" column="s_id" javaType="Student" select="findStudent"/>  
    </resultMap>  
    <select id="findStudent" parameterType="Blog" resultType="Student">  
        select * from student where id = #{sId}  
    </select>  
    <select id="getBlog" resultMap="BlogStudent">  
        SELECT * FROM blog  
    </select>  
    <insert id="addBlog" parameterType="Blog" useGeneratedKeys="true" keyProperty="id">  
        INSERT INTO blog (s_id, title, time)  
        VALUES (#{sId}, #{title}, #{time})  
    </insert>  
</mapper>
```
collection 使用
一对多映射 
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.mybatis.test.mapper.TeacherMapper">
    <!-- 定义resultMap -->
    <resultMap id="teacherStudents" type="Teacher">
        <result column="id" property="id"/>
        <result column="name" property="name"/>
        <collection ofType="Student" column="id" property="students" select="findStudent" />
    </resultMap>
    <!--查询语句-->
    <select id="getTeacher" resultMap="teacherStudents">
        select * from teacher
    </select>
    <select id="findStudent" resultType="Student">
        select * from student where t_id = #{id}
    </select>
</mapper>
```
## resultMap 超级好用的
## 动态sql
若子句的开头为 “AND” 或 “OR”，_where_ 元素也会将它们去除。
### [mybatis-plus](https://baomidou.com/getting-started/)
https://baomidou.com/getting-started/
#### 处理类属性与数据库字段不一致
方法一：在实体类上使用`@TableField`注解，指定数据库字段名
```java
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
```xml
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
