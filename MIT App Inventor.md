
这是一个开发 android app 的一个在线平台，无需编写代码，从界面到逻辑全部图形化操作。这里是一个[教程](http://m.elecfans.com/article/1040270.html)
下面是教程的附带arduino端的代码：

```c
String a;
int led = 13;
void setup(){
    Serial.begin(9600);
    pinMode(led,OUTPUT);
}

void loop(){
    while(Serial.available()){
        a = Serial.read();
        Serial.println(a);
        if(a =="ON")
        {
            digitalWrite(led,HIGH);
        }
        if(a =="OFF")
        {
            digitalWrite (led,LOW);
        }
    }
}
```

这是我对照教程自己做的项目：[http://ai2.appinventor.mit.edu/?locale=en#5679637117403136](http://ai2.appinventor.mit.edu/?locale=en#5679637117403136)

下面是关于UDP扩展的 [文章](http://lucstechblog.blogspot.com/2019/03/udp-communication-part-iv-android-to-esp.html),下载对应的扩展文件，然后导入就可以使用了。
