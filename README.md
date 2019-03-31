# Spring-HelloWorld

### 利用IDEA搭建spring hello world程序

来记录一下利用IDEA搭建spring hello world程序的过程~~~

1.首先点击Create New Project

![creat new project](Spring-HelloWorld/pics/creat new project.PNG)

2.勾选Spring，然后点击next

![choose spring](Spring-HelloWorld/pics/choose spring.PNG)

3.设置项目路径以及名字

4.IDEA会自动下载Spring所需的jar包

![jar](Spring-HelloWorld/pics/jar.PNG)

5.创建HelloWorld.class

```java
public class HelloWorld {
    private String name;
    public void setName(String name) {
        this.name = name;
    }
    public void sayHello(){
        System.out.println("Hello: " + name);
    }
}
```

6.创建Main.class

```java
public static void main(String[] args) {
        //1、创建Spring的IOC容器的对象
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-config.xml");
        //2、从IOC的容器中获取Bean的实例
        HelloWorld helloWorld = (HelloWorld) ctx.getBean("helloworld");
        //3、调用hello方法
        helloWorld.sayHello();
    }
```

7.Spring配置文件：spring-config.xml

看到网上一些教程说这个文件会自动生成，但是我的工程并没有，是自己新建的

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
       
    <bean id="helloworld" class="HelloWorld">
        <property name="name" value="Spring"></property>
    </bean>
</beans>
```

8.运行

![result](Spring-HelloWorld/pics/result.PNG)

网上说红色的字是Spring输出的日志

参考：[https://blog.csdn.net/cflys/article/details/70598903](https://blog.csdn.net/cflys/article/details/70598903)

### Git过程记录

首先先生成一个README.md文件

echo "# Spring-HelloWorld" >> README.md

git init

git add README.md

git commit -m "first commit"

git remote add origin https://github.com/zdy2017110124/Spring-HelloWorld.git

git push -u origin master

在最后一步时出了一些问题，github push failed (remote: Permission to userA/repo.git denied to userB.)。关于这个问题的解决方式，请参照[https://blog.csdn.net/klxh2009/article/details/76019742](https://blog.csdn.net/klxh2009/article/details/76019742)