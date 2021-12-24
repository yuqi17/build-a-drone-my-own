

### 串口monitor,输入并send
```c++

  String readString;
  
  void setup(){
    Serial.begin(115200);
    pinMode(LED_BUILTIN,OUTPUT);
  }

  void loop(){
    while(Serial.available()){
      delay(3);
      char c = Serial.read();// 读取输入值
      readString += c;
    }
    if(readString.length > 0){
      Serial.println(readString);
      if(readString == "on"){
        ledOn();
      }
      if(readString == "off"){
        ledOff();
      }
      readString = "";
      }
  }
  
  void ledOn(){
    Serial.println("LED ON");
    Serial.digitalWrite(LED_BUILTIN, LOW);
  }
  
  void ledOff(){
   Serial.println("LED OFF");
   Serial.digitalWrite(LED_BUILTIN, HIGH);
  }
```

### plotter 是绘图器,用于读取引脚值进行绘图
```c++
  // helper function , 用于显示多个值的图,可以用数学函数比如三角函数,随机函数,也可以直接读IO口
  void plot(String label,float value, bool last){
    Serial.print(label);
    if(label != "")Serial.print(":");
    Serial.print(value);
    if(last == false) Serial.print(",");
    else Serial.println();
  }

  void setup(){
    Serial.begin(115200);
    randomSeed(analogRead(0));
  }
  
  void loop(){
    float sensor1 = 10 * analogRead(A0)/1024f;// 不一定要乘以10
    float sensor2 = 20 + 10 * analogRead(A0)/1024f;
    plot("sensor1", sensor1, false);
    plot("sensor2", sensor1, true);
    
    delay(10);
  }
  
  
```
