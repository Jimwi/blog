1. zookeeper 中的watch是干嘛用的
2. dubbo中的listeners是干嘛用的

progress 
1. dubbo-cluster 90%
2. dubbo-common  10%
3. dubbb-config  30%
4. dubbb-configcenter 10%    ***
5. dubbo-filter 0%  这个dubbo-rpc-api里面的filter是一样的。
6. dubbo-metadata-report 0%  ***
7. dubbo-monitor 0%   原理和dubbo-rpc-api里面的filter是一样的，在filter里面做的一些统计
8. dubbb-plugin 5%
    8.1 dubbo-qos 5%   QosProtocolWrapper  启动QosServer
9. dubbb-registry 90%
    9.1 dubbb-registry-api 90%
    9.2 dubbb-registry-zookeeper 90%
10. dubbb-remoting 10%
    10.1 dubbo-remoting-api 10%
    10.2 dubbb-remoting-netty4 60%
    10.3 dubbb-remoting-zookeeper 60%
11. dubbo-rpc  10%
    11.1 dubbo-rpc-api 10%  ProtocolFilterWrapper ProtocolListenerWrapper
    12.1 dubbo-rpc-dubbo 10%
12. dubbo-serialization 90%
    12.1 dubbo-serialization-api  90%
    12.2 dubbo-serialization-hessian2 90%
13. dubbb-container 100%
