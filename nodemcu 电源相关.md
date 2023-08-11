
1. [低功耗](https://www.yiboard.com/thread-1550-1-1.html) D0(GPIO16) 接 RST(使能端)
2. ESP.deepSleep(1000000);// 单位微妙 1毫秒 = 1000微秒 , 所以上面是1秒; 30e6 就是30秒

```
ESP8266运行时，ESP8266的RST引脚始终为高电平。但是，当RST引脚接收到LOW信号时，它将重新启动微控制器。
如果您使用ESP8266设置了深度睡眠计时器，则计时器结束后，GPIO 16将发送LOW信号。这意味着，GPIO 16连接到RST引脚后，
可以在设定的时间后唤醒ESP8266。
```

```c++

void setup() {  

Serial.begin(115200);  

Serial.setTimeout(2000);  // Wait for serial to initialize.
 while(!Serial) {

}
 // Deep sleep mode for 30 seconds, the ESP8266 wakes up by itself when GPIO 16 (D0 in NodeMCU board) is connected to the RESET pin

Serial.println("I'm awake, but I'm going into deep sleep mode for 30 seconds"); 

 ESP.deepSleep(30e6);
// Deep sleep mode until RESET pin is connected to a LOW signal (for example pushbutton or magnetic reed switch)
//Serial.println("I'm awake, but I'm going into deep sleep mode until RESET pin is connected to a LOW signal");
 //ESP.deepSleep(0);
}

void loop() {

} 
```

### 上载代码后，按RST按钮开始运行代码，然后将RST连接到GPIO16。ESP8266应该每30秒唤醒一次，并在串行监视器中显示一条消息 

2. [关闭esp8266](https://www.toutiao.com/article/7062619573568258564/ 关闭esp8266 ) 接GPIO5 VCC, GND, 把电平拉低就关机

3. [nodemcu 简介](https://www.yiboard.com/thread-1548-1-1.html#google_vignette)
4. VIN 引脚的原理图如下:
![image](https://github.com/yuqi17/build-a-drone-my-own/assets/10356819/aaeeae08-2910-408c-9e93-7d4c1cc70b27)

5. 上面的图说明了 普通引脚的3.3V 是不走 ```AMS1117 低压差线性稳压器```, 再加上引脚的最大承受压是3.6V,因此 3.7V的锂电池(通常不会有3.7V)可以给nodemcu 供电.
