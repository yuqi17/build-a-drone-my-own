### [nodemcu 和 esp8266的关系](http://www.taichi-maker.com/homepage/esp8266-nodemcu-iot/esp8266-nodemcu-tutorial-index/nodemcu-hardware/)
### [用nodemcu 开发wifi也可以给esp8266系列的芯片编程](https://www.bilibili.com/read/cv2186586/)
### [参考mac 上的配置](https://www.toutiao.com/i6798723641820316168/)
### [ch340 mac 版驱动](https://github.com/adrianmihalko/ch340g-ch34g-ch34x-mac-os-x-driver/raw/master/CH34x_Install_V1.5.pkg)是一种类似USB的串口，但是普通USB 口是供电口，不能识别为通信口，所以要安装驱动
### arduino -> preference -> settings -> additional boards manager urls (nodemcu 插件) ```http://arduino.esp8266.com/stable/package_esp8266com_index.json```
### tools => board arduino -> board manager -> 搜索 esp8266 选择 esp8266 byesp8266 community 安装
### tools => 将开发板选择为 nodemcu 1.0 esp 12e module
### 将nodemcu 插到电脑上， tools 中选择这个新出现的 com 口
### 一段测试板子是否正常的代码
```c
#include "ESP8266WiFi.h"

const char* ssid = "ssid"; //输入你的wifi名（esp8266只支持2.4Gwifi!）
const char* password = "password"; //输入你的wifi密码

void setup(void)
{ 
  Serial.begin(115200);
  // Connect to WiFi
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) 
  {
     delay(500);
     Serial.print("*");
  }
  
  Serial.println("");
  Serial.println("WiFi connection Successful");
  Serial.print("The IP Address of ESP8266 Module is: ");
  Serial.print(WiFi.localIP());
}

void loop() 
{
  // EMPTY
}
```

### 上传代码到nodemcu,稍等片刻,大概10秒钟。对应的wifi必须存在才会打印信息。
总结一下：
### 1. 默认上面的写法是STA模式，相当于芯片去连接 wifi AP(路由器，或者热点）
### 2. 上面的 WiFi.localIP() 返回的就是芯片被 wifi AP 分配的IP,通常是不会自己改变的，估计是为了连接方便设置的固定静态IP。
### 3. Serial.begin(115200); 设置的baud 一定要和 serial monitor 上的 一样才不会出现乱码
### 4. 手机开热点可以不用接互联网网口wifi 或 移动流量也可以连芯片，它们是互不干扰的。
### 5. arduino 里面的String s = "xxx" 和 char *c = "xxx" char [] ssid = "xx" 不可以随便等同，String 是一个c++ 类
### 6. udp 模块读的API 可以是int, char[], String,但发送只能string, char[]

### 给esp 12f 编程：[这里提供了三种方法](https://www.youtube.com/watch?v=_iX67plFeLs&t=99s) , 我个人认为都不是很方便，还需要焊接，焊接了还要拆就比较麻烦了。如果不想
这么麻烦还是买一个烧写架 40元左右得了，可插拔的那种。
