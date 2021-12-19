

### [小程序 udp](https://www.jianshu.com/p/97b8f905d902)
关键点是发送给芯片的是字节数据 ```new Uint8Array()```, 这样才能被arduino 那边的SDK解析
