### 不建议使用的引脚
- 程序烧写时，会使用到TXD0\RXD0\GPIO0 三个引脚，如需使用，请烧写完成后，再连接外设使用。
- esp8266模块内部使用了一些IO，如S1\S2\S3\SC\SO\SK\GPIO15，编程时请不要调用，否则可能造成程序运行错误
### 参考图片:
 ![df853f1977a2e50be2879604e8958d6](https://github.com/yuqi17/build-a-drone-my-own/assets/10356819/d68a9f06-44cf-4572-b995-0de32ae9fd1e)
![79c48bd586a41c8eb1735a0a65879a2](https://github.com/yuqi17/build-a-drone-my-own/assets/10356819/377bfadc-96ef-4885-a3da-c4f0594f09f2)
![nodemcu_schematic](https://github.com/yuqi17/build-a-drone-my-own/assets/10356819/cadaa918-abaa-4043-ad4e-a79eac887e48)

### 可以知道:
TXD0 => GPIO1 => TX
RXD0 => GPIO3 => RX

// 以下为猜测:
S1 => SPI_CS1 => GPIO1 => TX
S2 => SPI_CS2 => GPIO0 => D3
S3 => SPI_CS0 => GPIO11 => CMD

SC , SO  , SK

GPIO15 => D8

可以确定: GPIO 0 , 1, 3, 15 最好不用于控制

#### NodeMCU V3上，内置LED的引脚为GPIO2，对应的引脚编号为D4  

好了还是看这个吧: [参考](https://zhuanlan.zhihu.com/p/433461900)
