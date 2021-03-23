# 智能急救头盔

## 项目描述

基于“安全出行，智能应用”的设计理念，我们研发了一款智能急救头盔。其不仅具有普通防护功能，还能够进行智能车祸检测，为伤者进行智能呼救并且采集事故现场图片用于交通事故处理。

我们采用软硬件结合的设计思想，运用嵌入式技术、智能硬件技术结合互联网技术等研发了智能急救头盔。其实现的主要功能有防护功能、智能呼救功能、实时车祸检测系统、图像采集与存储系统、数据无线传输体系、智能唤醒系统等。

## 运行环境

1. **CPU芯片:** STM32F103ZET6
2. **开发环境:** Keil Uvision 5.26
3. **编程语言:** C语言

## 目录说明

1. **code/Doc:** CPU引脚与端口说明
2. **code/ff11a:** 基于SD存储卡的FatFs文件系统, 移植到STM32
3. **code/Libraries:** 与CPU型号所对应的公用库
4. **code/Project:** 工程文件
5. **code/SYSTEM:** 一些与系统相关的方法，如软件延迟、硬件延迟、串口初始化等
6. **code/User:** 项目开发过程中所创建的文件，包含六轴传感器、红外传感器、GPS、GPRS、蓝牙、摄像头、蜂鸣器等模块源码

## 系统流程

1. 驾驶员带上智能急救头盔，触发红外传感器检测
2. 退出休眠模式，内核开始工作，所有外部传感器开始通电，并进行一系列初始化
3. 六轴传感器实时检测驾驶员的加速度、角速度等信息，当数据出现异常时，触发报警功能
4. 摄像头模块开始采集周围图像信息，GPS定位模块开始采集GPS信息，GPRS模块开始工作
5. GPRS模块通过SIM卡，注册到网络中，并将图像、GPS信息发送至服务端
6. GPRS模块通过SIM卡，发送手机短信到紧急联系人中
6. 蓝牙模块将图像、GPS信息发送至移动端
7. 蜂鸣器开始报警
8. 车祸检测流程结束

注：若驾驶员摘下智能急救头盔，则触发红外传感器检测，进入休眠模式，内核停止工作，通过继电器使得所有外部传感器全部断电，以尽可能地节省电源。