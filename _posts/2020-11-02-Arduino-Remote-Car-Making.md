---
layout: default
title:  "我的遥控小车制作"
my_date: 2020-11-02
tags: arduino DIY
---

### 我的遥控小车制作  
- 在网上买了小车硬件、各类传感器、焊台、胶枪、电池等之后，周末终于开始组装小车了。为什么要做，矫情点是放不下，又或许因为想从小事开始找一找不断实现目标的感觉。  
- 让我惊讶的是，常用芯片传感器型号还能依稀记得：L298N、1838红外、直流电机等。为什么选择Arduino？拥抱开源拥抱的是什么？因为我想让想法快速变为现实，而不被一个个门槛拦下，这也是我学习Python的理由。由于前面的积累，测试过遥控器和红外接受程序、测试过基本的串口通信，也了解了L298N驱动的接口，所以信心满满。  
- 硬件上，没有钻孔设备，硬件基本靠胶枪了，原则是不打架，比如考虑Arduino的电源线插头易于插拔，开关便于操作等。电机是6V直流电机，所以驱动板的输入用了4节5V电池，考虑单独给Arduino供电9V（查资料其供电范围较宽，供电5V时，IO口一般是3.3V），买的驱动板上的跳线插的作用也了解了，接上电测试最简单程序时候，
驱动板得电，但是电机不转，最后知道两个电源的负极需要接到一起共地，经验教训供参考。  
- 其次是编程，Arduino的编程不熟悉，基本离不开官网的Reference，查看语法，比如表比较是“==”，而不是“=”，比如红外收到的数据格式是十六进制还是十进制等等，基本编程一是经验，二是细心，还需要有小到大，
先测试最小功能，再最终实现所有，善于查找错误。  
- 最后是逻辑，遇到的槛是，我需要长按命令生效，而测试时出现按下后，不主动停止，通过梳理程序，发现是逻辑问题，尤其是如何区分长按结束和收到两个信号间的空闲，最后通过串口测试信号之间时差，选择了200ms，当然查阅红外协议可以更严谨。还有就是当时的红外程序，即使不再接收到数据，数据变量不会清零，而是保持上次收到的值，因此我在网络源程序的判断收到新数据处加上了标志位的赋值，也是供参考。  
- 其他嘛，驱动板的EN以后可以改成PWM；硬件用的两个驱动轮和一个万向轮，由于万向轮转动阻力大，会使转向有偏差，可以改为两个驱动轮，两个转向轮，甚至像朋友所说，加上差速器。  
- 嘛，很满意，虽然有时候问自己，做这样简单的东西感到高兴这件事本身究竟可不可悲，甚至会不会显得可怜？不知道，也许，只要不停下，一直向前走，会见到相见的人和事的吧。