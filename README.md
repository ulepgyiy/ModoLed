# ModoLed
Modo handlamp based on atmega328 , use Arduino Fio and RGB or RGBW led.
#魔豆LED（ModoLed）

##设计功能

###1.编码器按键行为
编码器可以检测长按、短按、连续多按的用户行为，MCU可以切换关机（低功耗并关闭所有外围设备），开关机切换可以通过三连击编码器按钮来切换，由于在意外情况下，外部物体可能碰到编码器按键，容易导致意外短按或长按编码器，但一般不容易实现三连击操作，这钟设计尽可能减小了意外开灯耗电的情况，但是如果用户更喜欢也更习惯双击或长按操作的话，也可以通过修改代码实现其他操作模式开机效果。

设计代码中，当用户关机状态下进行非开机的其他所有操作，MCU将忽略并继续低功耗，在开机状态下，用户双击编码器会切换灯光的工作模式，常见的工作模式有照明模式、呼吸模式、流水模式等等，在某个模式下，用户长按编码器会使灯光进入设置状态，在设置状态下通过旋转编码器可以调整灯光的相关参数，如光色、亮度、频率等，设置模式下短按编码器会切换设置参数内容，比如本来在设置白光亮度，短按一下后再旋转编码器就会设置彩色光亮度了，设置状态下长按编码器会切换回工作状态。

用户拿到灯光后，通过三击编码器可以开机，手电筒会自动亮起来，进入上次关机前的工作模式，用户可以通过双击切换功过模式，也可以通过长按编码器进入设置模式对当前工作模式相关参数进行设置相关参数，设置完成后相关参数会被保存到EEPROM中。

###2.灯光响应状态指示



##实现方法

##芯片引脚功能定义

##自定义代码的方法

>#define EC11A_PIN 2  //中断0 编码器A引脚
>#define EC11B_PIN 4  //编码器B引脚
>#define EC11W_PIN 3  //中断1 编码器KEY引脚
>#define LED1_POWER_PIN 7  //灯条1的供电控制引脚 置1开启供电
>#define LED2_POWER_PIN 10  //灯条2的供电控制引脚 置1开启供电
>#define LED_DATA_PIN    5  //LED灯条的数据控制引脚 VER1版本设计硬件中两个灯条共享数据引脚
>#define TEMPERATURE_PIN A3   //温度传感器AD输入引脚
>#define  TEMPERATURE_EN_PIN  9  //温度传感器取电引脚
>#define  BATTERY_VOLTAGE_PIN  A0  //电池电压采集引脚
>#define  USB_VOLTAGE_PIN  A2    //USB充电状态电压采集引脚

##更新固件注意事项，常见问题和解决方法
