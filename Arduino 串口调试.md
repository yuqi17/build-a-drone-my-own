

### 串口monitor,输入并send
```

  String readString;
  
  void setup(){
    Serial.begin(115200);
    pinMode(LED_BUILTIN,OUTPUT);
  }

  void loop(){
    while(Serial.available()){
      delay(3);
      char c = Serial.read();
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
