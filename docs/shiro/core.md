### aop模块

​		有三个接口

1. ```java
   1. MethodInterceptor 拦截器 
   
   2. AnnotationResolver 获得某个方法上的注解
   
   3. AnnotationHandler 处理注解
   
   4. MethodInvocation 保存被切的方法的上下文
   
   ```

`AnnotationHandler`有个一个子类 `AuthorizingAnnotationHandler`

