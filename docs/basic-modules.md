# 常见模拟量与开关量模块

[返回首页](../README.md) · [传感器驱动](sensors.md) · [其他外设](peripherals.md)

这类模块常见于入门套件：许多只需 ADC 或 GPIO 即可读取，不一定需要独立驱动库。下表链接是具体模块的厂商教程和示例，**不代表所有同名模块的电路、电压、引脚或代码都相同**；使用例程前请检查页面和关联代码的许可。

| 模块 | 输出 / 资料 | 使用提示 |
| --- | --- | --- |
| 土壤湿度 | 模拟量：[Grove Moisture Sensor](https://wiki.seeedstudio.com/Grove-Moisture_Sensor/) | ADC 原始值要按土壤、供电和传感器标定；电阻式探头长期通电可能腐蚀 |
| 漏水 / 雨水检测 | 模拟量或数字量：[Grove Water Sensor](https://wiki.seeedstudio.com/Grove-Water_Sensor/) | 该例程对应指定 Grove 版本，先确认输出电压与 ADC/GPIO 范围 |
| 水位检测 | I²C：[Grove Water Level Sensor](https://wiki.seeedstudio.com/Grove-Water-Level-Sensor/) | 该模块并非所有水位模块的通用协议；确认安装和量程 |
| 人体红外感应 PIR | 数字量：[Grove PIR Motion Sensor](https://wiki.seeedstudio.com/Grove-PIR_Motion_Sensor/) | 检测运动引起的红外变化，不等同于持续判断有人无人；留意预热和保持时间 |
| 火焰传感器 | 数字量：[Grove Flame Sensor](https://wiki.seeedstudio.com/Grove-Flame_Sensor/) | 结果受光照、距离和模块阈值影响；不能直接作为可靠消防报警设备 |
| 水中 TDS | 模拟量：[Grove TDS Sensor](https://wiki.seeedstudio.com/Grove-TDS-Sensor/) | 按例程和探头做校准及温度补偿；TDS 不能单独证明水可饮用 |

## 接线与读数

- 模拟输出接 MCU ADC 前，先查模块输出范围是否超过 ADC 允许电压；分压、供电或电平转换必须按实际硬件设计。
- 数字输出先查高低电平、电压及是否为开漏输出。比较器模块的电位器通常只改变数字触发阈值，不能直接替代标定。
- ADC 数值受参考电压、分辨率、供电、噪声和采样方式影响；平均滤波可以抑制部分噪声，但不能代替校准。
- 水位、土壤、火焰和气体模块的名称很泛，购买时优先确认电路、接口、输出类型及供应商资料。
