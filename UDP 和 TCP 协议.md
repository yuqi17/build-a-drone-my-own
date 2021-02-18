
### [java udp tcp](https://www.jianshu.com/p/cc62e070a6d2)
### [小程序 udp](https://www.jianshu.com/p/97b8f905d902)

### 在mac os 上自带有netcat 网络通信模块。可以用命令行进行调试：
```shell
  echo "hello,server"  | nc -4u localhost 8888
```
我试过了用本机的路由分配地址无法发送信息。而localhost 和 127.0.0.1 实际上是一个东西。
### 可以用 tcpdump 命令观察数据传送的情况，需要一定的授权。
