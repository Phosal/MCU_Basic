### 什么是GPIO

- GPIO,**通用输入输出端口**,简单来说就是STM32可控制的引脚,STM32芯片的GPIO引脚与外部连接起来,从而实现与外部通讯、控制以及数据采集的功能
- 我们可以控制GPIO引脚的电平变化,达到我们的各种目的

### GPIO内部结构

<img src="D:\Code\MarkdownNote\MCU_Basic\文档所用图片\GPIO图解1.png">
<img src="https://github.com/Phosal/MCU_Basic/blob/master/%E6%96%87%E6%A1%A3%E6%89%80%E7%94%A8%E5%9B%BE%E7%89%87/GPIO%E5%9B%BE%E8%A7%A31.png">
<img src="D:\Code\MarkdownNote\MCU_Basic\文档所用图片\GPIO图解2.png">
<img src="https://github.com/Phosal/MCU_Basic/blob/master/%E6%96%87%E6%A1%A3%E6%89%80%E7%94%A8%E5%9B%BE%E7%89%87/GPIO%E5%9B%BE%E8%A7%A32.png">

- 输出数据寄存器作用于最普遍的GPIO引脚高低电平控制
- 复用功能输出是让USART TIMER之类的外设来操控引脚高低电平
- 输入数据寄存器对应输出数据寄存器，作用于最普遍的读取外界电平
- 肖特基触发器右侧的VDD和VSS则可作用于输入浮空、输入上拉、输入下拉
- 复用功能输入是让引脚功能复用，让一些外设读取引脚高低电平
- 模拟输入不经过肖特基触发器，信号不会被变为离散信号，可以读取模拟信号
- 肖特基触发器可以将连续信号变为离散信号

### GPIO两种输出结构

<img src="D:\Code\MarkdownNote\MCU_Basic\文档所用图片\GPIO输出结构.png">
<img src="https://github.com/Phosal/MCU_Basic/blob/master/%E6%96%87%E6%A1%A3%E6%89%80%E7%94%A8%E5%9B%BE%E7%89%87/GPIO%E8%BE%93%E5%87%BA%E7%BB%93%E6%9E%84.png">

- 推挽输出可以直接通过IN的高低电平来控制OUT的高低电平
- 开漏输出没有办法直接通过IN的高电平来让OUT输出高电平，必须凭借上拉电阻才能输出高电平，输出低电平与推挽输出类似(开漏输出无法真正输出高电平，高电平时没有驱动能力)
- 推挽输出虽然不需要额外的辅助电路，但是输出电压固定，与cpu电源电压相等。而开漏输出可以上拉一个不同于cpu电源的电压，可大可小，对于只接受3.3v的stm32来说，使用开漏输出可以让引脚获得输出5v。此外，开漏输出还可用于I2C的总线，判断总线占用状态；匹配不同外设所需的电平(不同于cpu电源的电平)

<img src="D:\Code\MarkdownNote\MCU_Basic\文档所用图片\GPIO输出结构区别.png">
<img src="https://github.com/Phosal/MCU_Basic/blob/master/%E6%96%87%E6%A1%A3%E6%89%80%E7%94%A8%E5%9B%BE%E7%89%87/GPIO%E8%BE%93%E5%87%BA%E7%BB%93%E6%9E%84%E5%8C%BA%E5%88%AB.png">