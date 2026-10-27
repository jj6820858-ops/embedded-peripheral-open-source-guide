# 通用资源与学习路径

[返回首页](../README.md)

## 资源聚合

| 资源 | 平台 | 适合查什么 |
| --- | --- | --- |
| [ESP-IoT-Solution](https://github.com/espressif/esp-iot-solution) | ESP-IDF | 乐鑫官方外设组件、示例、中文文档 |
| [ST MEMS Standard C drivers](https://github.com/STMicroelectronics/STMems_Standard_C_drivers) | 可移植 C | ST MEMS 运动和环境传感器，需对接读写回调 |
| [Zephyr 传感器示例](https://docs.zephyrproject.org/latest/samples/sensor/sensor.html) | Zephyr | 设备树配置、传感器 API 和示例 |
| [Zephyr 驱动示例](https://docs.zephyrproject.org/latest/samples/drivers/drivers.html) | Zephyr | 显示、存储等各类驱动用法 |
| [RT-Thread 软件包索引](https://github.com/RT-Thread/packages) | RT-Thread | 软件包元数据与实际源码链接 |
| [Adafruit CircuitPython Bundle](https://github.com/adafruit/Adafruit_CircuitPython_Bundle) | CircuitPython | 大量外设 Python 驱动；不保证 MicroPython 兼容 |
| [SparkFun GitHub](https://github.com/sparkfun) | 多平台 | 模块资料、Arduino 驱动及示例 |
| [Arduino 库索引](https://www.arduinolibraries.info/) | Arduino | 按型号检索库和版本 |
| [Linux IIO 文档](https://docs.kernel.org/driver-api/iio/index.html) | Linux | Linux 传感器子系统 |

## 按主控和框架查片上外设例程

片上 UART、I²C、SPI、ADC、定时器的驱动与板外传感器驱动是两层：先根据主控 SDK 配好总线，再接入与传感器型号匹配的驱动。SDK 内不同组件可能使用不同许可证，请按实际使用的文件核对。

| 平台 | 源码和例程入口 | 提示 |
| --- | --- | --- |
| 8051 / STC8 | [mcs51-ell](https://github.com/gevico/mcs51-ell) · [uni-STC](https://github.com/area-8051/uni-STC) | 前者覆盖增强型 8051 和 STC8 例程；后者面向 SDCC，不能默认兼容 Keil；均需确认芯片型号 |
| STM32 | [STM32Cube 各系列入口](https://github.com/STMicroelectronics/STM32Cube_MCU_Overall_Offer) · [STM32CubeF1](https://github.com/STMicroelectronics/STM32CubeF1) | 选择 MCU 对应系列、板卡及 HAL/LL 版本；留意仓库子模块 |
| MSPM0 | [TI MSPM0 SDK](https://github.com/TexasInstruments/mspm0-sdk) | 查 DriverLib、SysConfig 和对应板卡例程；重新生成配置时避免手改生成文件 |
| ESP32 | [ESP-IDF examples](https://github.com/espressif/esp-idf/tree/master/examples) | 按具体芯片和 IDF 版本选择片上外设示例 |
| Zephyr | [BME280 传感器示例](https://github.com/zephyrproject-rtos/zephyr/blob/main/samples/sensor/bme280/README.rst) | 结合板卡设备树、overlay、Kconfig 与 sensor API |
| RT-Thread | [Env 使用文档](https://github.com/RT-Thread/rt-thread/blob/master/documentation/env/env.md) · [软件包索引](https://github.com/RT-Thread/packages) | 使用 menuconfig 和软件包工具；确认包版本和 BSP |
| MicroPython | [SSD1306 官方驱动](https://github.com/micropython/micropython-lib/blob/master/micropython/drivers/display/ssd1306/ssd1306.py) | 按板卡构造 I²C/SPI；MicroPython 与 CircuitPython 库不保证互通 |
| Raspberry Pi Pico | [Pico SDK 示例](https://github.com/raspberrypi/pico-examples) | C/C++；有多种外设例程，检查板型和 PIO 资源 |
| ESP-IDF 第三方驱动 | [esp-idf-lib 新组件入口](https://github.com/esp-idf-lib/core) · [旧版集合（已归档）](https://github.com/UncleRus/esp-idf-lib) | 新旧组件均需核对许可证、芯片和 ESP-IDF 版本；旧集合已停止维护 |
| STM32duino | [Arduino Core STM32](https://github.com/stm32duino/Arduino_Core_STM32) · [STM32Examples](https://github.com/stm32duino/STM32Examples) | STM32 的 Arduino 支持；选用已支持的板卡和版本 |

## 一套通用上手流程

1. **确认器件**：识别芯片型号、模块版本、供电范围和支持的总线。查看原厂数据手册和模块原理图。
2. **确认硬件**：共地，检查 3.3 V / 5 V 和 IO 电平；I²C 检查上拉、地址和总线电容；SPI 核对片选、模式与频率；UART 核对波特率和 TX/RX。
3. **确认环境**：匹配 MCU、框架、编译器和库版本。先阅读项目 README、examples 与许可证。
4. **最小验证**：例如 I²C 扫描地址、读芯片 ID，再按例程初始化并读取数据；显示屏先显示简单图形。
5. **移植调试**：实现底层读写、延时、GPIO 和必要的锁；明确字节顺序、超时、单位、校准和错误处理。
6. **记录结果**：记下芯片和模块版本、接线、电源、地址、软件版本及实测现象，便于复现。

## 新手推荐顺序

GPIO 点灯/按键 → UART 打印 → I²C 扫描 → SSD1306 显示 → 温湿度传感器 → SPI 屏幕/存储 → IMU 与中断 → 无线通信 → 电机控制。

传感器读数会受供电、布线、校准和环境影响；传感器模块和电机驱动板的电气设计也不同。以数据手册和具体板卡原理图为准。
