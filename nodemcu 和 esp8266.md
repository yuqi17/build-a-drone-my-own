### [nodemcu 和 esp8266的关系](http://www.taichi-maker.com/homepage/esp8266-nodemcu-iot/esp8266-nodemcu-tutorial-index/nodemcu-hardware/)
### [淘宝及简介](https://detail.tmall.com/item.htm?spm=a220m.1000858.1000725.5.5b742cd5KibsEt&id=606082163513&user_id=2201438661052&is_b=1&cat_id=2&q=nodemcu&rn=a9b6ddf99cecfa5c01e0482d98eb40d4)
### [nodemcu 连接mac 版 arduino ide](https://www.youtube.com/watch?v=G0LGr1WpkdQ)
### [参考mac 上的配置](https://www.toutiao.com/i6798723641820316168/)
### [ch340 mac 版驱动](https://github.com/adrianmihalko/ch340g-ch34g-ch34x-mac-os-x-driver/raw/master/CH34x_Install_V1.5.pkg)
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
  Serial.print(WiFi.localIP());// Print the IP address
}

void loop() 
{
  // EMPTY
}
```

### 上传代码到nodemcu,稍等片刻
### tools serial monitor 串口监听器，按一下板子上的 RST 重置按钮，看看是否返回对应的字符串

