### 0. 简要说明
该目录下的JSON文件一般由三部分组成，request header， request body和responsebody。 request header和request body需要TrustIE生成。并向Eclipse Che发送。

样例中的Che端口为 172.17.0.1，端口8080，上述两处可依据实际情况替换。

Eclipse Che 所需端口 8080, 5050, 32768-65535，其中官方文档可改。[Che官方文档如是说](https://www.eclipse.org/che/docs/che-6/docker-multi-user.html)

RestAPI接口在<CHE_HOST>:<CHE_PORT>/api/swagger/ 下

### 1. 发送创建Workspace的请求
通过Post方式调用Restful API，创建Workspace。Workspace具体可分为两类：一类为持久化的Workspace，另一类为临时Workspace。持久化Workspace被停止后可保留，临时Workspace停止后被删除。临时Workspace不会显示在Web界面的Workspace列表中。

两种Workspace创建方法在step1.1和step1.2中。友情提示可以修改对应project的url来引入不同项目。query中的start-after-create字段可根据需要设置

### 2. redirect
获取到response body中的links.ide字段，将页面重定向到该url处，即可看到eclipse che的ide界面，开始编辑。

### 3. ？？
通过调用runtime的restful api可以启动或停止workspace

### 4.
可以通过step 0中的get Workspace来获取当前所有的Workspace的信息，再通过3中的对runtime的资源的控制来删除不必要的Workspace。