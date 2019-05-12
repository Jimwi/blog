# zookeeper 命令

## zkCli.sh 登录服务端

1. `./zkCli*sh -timeout 3000 -server localhost:2181 -r`  
    `-r readonly`  
    默认 -timeout 3000 -server localhost:2181
  
2. `ls path [watch]`  
    列出指定节点下的所有一级子节点。

3. `ls2 path [watch]`  
    ls + stat

4. `get path [watch]`  
    列出节点的数据 + stat

5. `set path data [version]`  
    给节点添加数据或者修改节点的数据。

6. `create [-s] [-e] path data acl`  
    创建节点  
    `-s:` 表示节点为顺序节点  
    `-e:` 表示节点为临时节点  
    `acl:` 访问控制列表  

7. `delete path [watch]`  
    删除节点

8. `stat path [watch]`
列出节点信息  

    |key|value|
    | -- | -- |
    |`cZxid = 0x31`|节点被创建时的事物的ID|
    |`ctime = Sat Mar 16 15:38:34 CST 2019`|创建时间|
    |`mZxid = 0x31`|节点最后一次被修改时的事物的ID|
    |`mtime = Sat Mar 16 15:38:34 CST 2019`|最后一次修改时间|
    |`pZxid = 0x31`|子节点列表最近一次呗修改的事物ID|
    |`cversion = 0`|子节点版本号|
    |`dataVersion = 0`|数据版本号|
    |`aclVersion = 0`|ACL版本号|
    |`ephemeralOwner = 0x0`|创建临时节点的事物ID，持久节点事物为0|
    |`dataLength = 22`|数据长度，每个节点都可保存数据|
    |`numChildren = 0`|子节点的个数 |

9. `listquota path`  
    列出节点的限制

10. `setquota -n|-b val path`  
    设置节点的限制  
    `-n:` 表示子节点的最大个数  
    `-b:` 表示数据值的最大长度  

11. `delquota [-n|-b] path`  
    删除节点的限制  

12. `setAcl path acl`  
    设置节点的权限  
    acl格式:  `schema:id:permision`  
        `schema:` ip|digest  
        `id:` ip|userName:string  
        `string:` 字符串，通过一定规则得到的  
        `permision:` crwda  
        `c:` create 创建子节点  
        `r:` read 获得节点数据和子节点列表  
        `w:` write 更新节点数据  
        `d:` delete 删除子节点  
        `a:` admin 设置节点的ACL  

13. `getAcl path`  
    获得节点的权限的列表  

14. `sync path`  

15. `rmr pat`  
    递归删除节点  

16. `printwatches on|off`  

17. `addauth scheme auth`  
    注册会话授权信息  
    `schema: ip:digest`  
    `auth: ip|username:password `

18. `history`  
    历史命令  

19. `redo cmdno`  
    重新执行命令* cmdno为 history输出的命令号  

20. `quit`  
    退出客户端  

21. `close`  
    关闭连接，不退出可客户端  

22. `connect host:port`  
    连接服务端  
