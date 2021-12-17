操作系统安全加固工具



集群管理：

主机：serve启动端口TCP监听节点加入，校验证书或密码，每个节点加入集群后分配单独的TCP连接。

节点：通过join IP:port (pwd)的方式与master节点通信，经校验后分配TCP连接加入集群。

通信：使用非对称加密的方式加密对称加密密钥，完成密钥传输后正式加入集群，分发指令和收集返回值使用对称密钥进行加密。确保指令不能被转发执行。



配置文件存储到`/etc`目录下，以JSON格式记录连接的节点信息和创建的安全规则等。

日志信息存储到`/var/log`目录下。master节点日志存储，记录peer节点执行结果；peer节点记录连接记录、指令执行历史和执行结果。

指令执行：

```Go
// Without result.
cmd := exec.Command("ls", "-a")
err := cmd.Run()
if nil ！= err {
    log.Fatal("Error: " + err.Error())
}

// With result.
cmd := exec.Command("ls", "-a")
out, err := cmd.ComninedOutput()
if nil != err {
    log.Panic("Error: " + err.Error())
}
fmt.Println(out)

// Pipe
c1 := exec.Command("grep", "ERROR", "/var/log/messages")
c2 := exec.Command("wc", "-l")
c2.Stdin, _ = c1.StdoutPipe()
c2.Stdout = os.Stdout
```





Supervisor 守护进程。https://cloud.tencent.com/developer/article/1665596 (应该不需要)



Level, scene, detect, setting.

Log module.

RPC remote using. Cluster leader and nodes. Remote SSH.

User interfaces. (Local using)



CP-ABE KP-ABE using in Communication and log system.

https://blog.csdn.net/jingzi123456789/article/details/104783728

https://cloud.tencent.com/developer/article/1682470

https://cloud.tencent.com/developer/article/1682597

[CP-ABE] http://acsc.cs.utexas.edu/cpabe/index.html



Log redirect https://blog.csdn.net/smilesundream/article/details/83867559

https://zhuanlan.zhihu.com/p/245369778

goroutine channel waitGroup



Go + C https://www.cnblogs.com/linguanh/p/8323487.html

https://www.jianshu.com/p/ce97accb1801



