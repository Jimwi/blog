# ApplicationConfig

```xml
<dubbo:application name="demo-application" version="1.0.0" owner="xun" organization="qudian" architecture="" environment="dev" compiler="javassist" logger="slf4j" monitor="" registry=""/>
```


#### compiler
compiler是Dubbo生成动态代理的时候使用的技术。见org.apache.dubbo.common.compiler.Compiler拓展。Dubbo提供了两种实现JdkCompiler，JavassistCompiler的实现



logger是dubbo的日志输出方式，见org.apache.dubbo.common.logger.LoggerAdapter拓展，Dubbo提供了jcl，jdk，log4j，log4j2，slf4j的实现







