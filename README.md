# 嵌入式外设开源资料导航

面向单片机、嵌入式 Linux 和物联网学习者的外设资料索引：从 OLED、LCD、传感器到无线通信、存储和电机控制，帮助你按**芯片型号、通信接口和开发平台**找到开源驱动、例程与文档。

> 本仓库是资料导航，不包含各项目的驱动源码。收录表示有参考价值，不表示已经在你的硬件上验证。最近整理于 2026-10-27；版本、维护状态和链接可能变化，请以原项目为准。

## 目录

- [传感器：环境、运动、距离、光学、气体、电量等](docs/sensors.md)
- [显示、输入、通信、存储、音频、电机等外设](docs/peripherals.md)
- [常见模拟量与开关量模块：土壤、漏水、人体感应等](docs/basic-modules.md)
- [STM32 与 ESP32 驱动和例程专题](docs/stm32-esp32.md)
- [通用资源与学习路径](docs/learning.md)

## 不知道从哪里开始？

1. 先看模块背面的芯片丝印和接口，确认是 **SSD1306** 还是 SH1106、I²C 还是 SPI；外形相似不等于驱动兼容。
2. 在资料表中搜索型号，优先打开与你的开发平台对应的库，阅读其 README、示例和依赖。
3. 检查电源电压、电平、引脚、I²C 地址、上拉电阻和 SPI 时序；先运行最小示例，再移植到自己的工程。
4. STM32、MSPM0、STC/8051 等使用 Arduino 库时，一般需要移植总线、延时和 GPIO；ESP-IDF、Zephyr、RT-Thread 项目也依赖各自框架，不能直接当成通用 C 文件。
5. 使用前阅读源项目的许可证和数据手册；保留必要的版权与许可声明。链接可访问不代表代码已通过本仓库的编译或实物测试。

## 按平台找资源

| 平台/方向 | 推荐入口 | 用途 |
| --- | --- | --- |
| ESP32 / ESP-IDF | [ESP-IoT-Solution](https://github.com/espressif/esp-iot-solution) · [中文文档](https://docs.espressif.com/projects/esp-iot-solution/zh_CN/latest/) · [组件仓库](https://components.espressif.com/) | 官方传感器、显示、输入、执行器组件及示例 |
| STM32 / 可移植 C | [ST MEMS 标准 C 驱动](https://github.com/STMicroelectronics/STMems_Standard_C_drivers) | ST 运动、环境等传感器的底层驱动；需要实现平台读写接口 |
| Arduino | [Arduino Library Manager 列表](https://www.arduinolibraries.info/) · [Adafruit 库](https://github.com/adafruit) · [SparkFun 库](https://github.com/sparkfun) | 入门示例多，移植到其他平台需要适配 |
| Zephyr | [驱动示例](https://docs.zephyrproject.org/latest/samples/drivers/drivers.html) · [传感器示例](https://docs.zephyrproject.org/latest/samples/sensor/sensor.html) | 结合设备树、Kconfig 和驱动 API |
| RT-Thread | [软件包索引](https://github.com/RT-Thread/packages) · [RT-Thread 内核](https://github.com/RT-Thread/rt-thread) | 在软件包索引中查找设备驱动与示例 |
| MicroPython / CircuitPython | [MicroPython 驱动](https://github.com/micropython/micropython/tree/master/drivers) · [CircuitPython 库集合](https://github.com/adafruit/Adafruit_CircuitPython_Bundle) | Python 外设驱动；两种运行时不保证互相兼容 |
| 嵌入式 Linux | [Linux 内核驱动](https://github.com/torvalds/linux/tree/master/drivers) · [IIO 文档](https://docs.kernel.org/driver-api/iio/index.html) | 内核驱动与工业 I/O 传感器框架 |

## 贡献

欢迎提交 Issue 或 Pull Request。新增时请给出：设备型号、功能、接口、支持平台、原始项目链接、示例入口和必要注意事项；优先使用官方或维护者原始仓库。不要直接搬运第三方代码，确需引入时先核对其许可证。
