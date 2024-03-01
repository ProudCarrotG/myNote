# 创建项目
使用 `idea` 自带的 Spring 项目创建工具
![项目创建工具](assets/Pasted%20image%2020240229224140.png)
在选择依赖项时选择需要的项目
![依赖项选择](assets/Pasted%20image%2020240229224302.png)
随后等待 `maven` 自动安装依赖项即可

# 入门操作
## 入口点
```java
@SpringBootApplication  //固定注解
public class $className${
	...
}
```
`@SpringBootApplication` 把一个类标记成了入口点，一个入口点独占一个**端口**，相当于在这个端口上部署了一个服务

当用户访问端口时，会执行入口点类中的操作

## 控制器 @RestController
`   @RestController` 是一个 Spring Framework 提供的注解，它结合了 `@Controller` 和 `@ResponseBody` 注解的功能。在 Spring MVC 中，`@Controller` 用于标识控制器类，而 `@ResponseBody` 用于指示方法的返回值应该直接作为 HTTP 响应的内容返回，而不是视图名称。

因此，`@RestController` 注解用于标识一个类是 RESTful Web 服务的控制器，并且其中的方法返回的是 JSON、XML 或其他类型的数据，而不是视图。它是一个方便的方式来创建 RESTful API。

### 响应类型方法

需要注解 `@<方法类型>Mapping`

在控制器类中的方法，用来标识该方法响应的是何种 http 请求，[http请求类型](../../网络/http/请求类型.md)；

#### <方法类型>
几乎能够响应[请求类型](../../网络/http/请求类型.md)中的所有，写法是首字母大写。例如：
```
@GetMapping
@PostMapping
```

其中，有一个注解能够包含其他这些注解：`Request`。默认下他能响应所有的请求，但也可以通过添加参数使其针对某种请求做出响应

```
@RequestMapping(value = "/hello", method = RequestMethod.GET)
//该种写法表示：注解下的方法仅对GET请求做出响应
```

#### Mapping
在 `@GetMapping` 中，`Mapping` 表示映射（Mapping），它指定了将 HTTP 请求映射到处理方法的规则。具体来说，`Mapping` 将 HTTP 请求中的路径（URL）与处理方法进行关联，当请求的路径与映射规则匹配时，Spring MVC 就会调用相应的处理方法来处理该请求。

在 `@GetMapping` 注解中，`Mapping` 部分指定了使用 HTTP GET 方法访问指定路径时，应该调用哪个处理方法。例如：


```
@GetMapping("/hello") 
public String hello() 
{     
	return "Hello, world!"; 
}
```

这里的 `@GetMapping("/hello")` 指示当访问路径为 "/hello" 且使用 HTTP GET 方法时，应该调用 `hello()` 方法来处理请求。因此，`Mapping` 在这里就是指定了请求路径与处理方法之间的映射关系。



# 配置文件
默认路劲为
```
/src/main/resources
```

直接放置于该路径下的配置文件将会优先加载

常用的配置文件为 `application.properties` , `application.yml`, `application.yaml`  (按加载优先级排序)

在配置文件中，有些内容是项目中的依赖定义好的，如果重新配置了，则覆盖默认内容；有些是允许自定义的

## .properties
这是 Java 中常见的属性文件格式，使用键值对的方式来表示配置属性。每一行都是一个属性，形式为 `key=value`。示例：
```
server.port=8080 
logging.level.root=INFO
```

## .yml and .yaml
这是 YAML（YAML Ain't Markup Language）格式的配置文件，它使用缩进和冒号来表示属性的层级关系。YAML 格式的配置文件更加易读和易写，尤其适合复杂的配置场景。示例：
```
server:
  port: 8080
logging:
  level:
    root: INFO

```

## 调用配置文件中的参数
### @value
在定义变量前使用注解
