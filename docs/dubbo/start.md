1. dubbo启动过程
  1.1. 服务端
        #  spring 读取配置文件，读取到<dubbo:service />的时候,会创建一个ServiceBean。
            ServiceBean是一个InitializingBean，创建完成后，spring会调用afterPropertiesSet()方法。
            afterPropertiesSet里面有export()方法，从而启动服务。注册服务。
        #  判断是否延迟加载，如果是延时加载，就创建一个定时任务。
        #  创建invoker。根据 ”接口真正的的实现“ 创建invoker
        #  创建exporter
                在invoker上加Filter
                在invoker上加Listener （Filter和Listener的顺序是不定的）
                通过invoker创建exporter，将exporter缓存起来
        #  启动netty服务端，（读取第一个<dubbo:service />是启动服务器）
        #  将exporter的信息注册到zookeeper上

  1.2. 客户端
        # spring 读取配置文件，读取到<dubbo:reference />的时候,会创建一个ReferenceBean。
          ReferenceBean是一个InitializingBean，创建完成后，spring会调用afterPropertiesSet()方法。
          afterPropertiesSet里面有getObject()方法，从而初始化客户端代理。
        # 创建代理
            # 为每一个interface创建一个RegistryDirectory。
            # 订阅zookeeper的注册信息。
            # 根据zookeeper注册的信息，创建invoker。
                通过dubboProtocol 创建netty客户端。
                创建invoker
                将nvoker保存到RegistryDirectory中。
            # 用cluster将directory中的invoker合成一个invoker，并缓存起来。
            # 创建invoker的代理。并缓存起来。