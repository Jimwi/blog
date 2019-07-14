# curator实现分布式锁

curator实现分布式锁的api在curator-recipes模块的org.apache.curator.framework.recipes.locks下

## 接口

1. InterProcessLock  分布式锁的接口，有3个实现

   ```java
   InterProcessMutex
   InterProcessReadWriteLock
   InterProcessSemaphoreMutex
   ```

2. Revocable

3. Lease

4. Revocable

5. RevocationListener

6. RevocationSpec

7. LockinternalsDriver 与zookeeper交互

8. LockInternalsSorter 对节点进行排序的

疑问：

1. 当线程A没有获得到锁，把路径删除的时候，监听A的线程的时候会不会以为线程A释放了锁。

2. 有序临时节点的命名其中有一段是用来表示节点顺序的 0000000000，一共10位，每次有新的线程尝试获取锁的时候，就会产生一个新的有序临时节点，名称在最大的序号后面加1，那么，这个数据超过长度怎么办？
