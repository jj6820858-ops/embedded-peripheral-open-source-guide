# STM32 与 ESP32 外设驱动专题

[返回首页](../README.md) · [按传感器查找](sensors.md) · [按其他外设查找](peripherals.md)

这里优先列出有具体平台代码的项目。表中“例程”表示上游提供的源码或使用示例，并不表示本仓库已完成编译、烧录或实测。不同 MCU 型号、开发板、芯片接口、时钟、工具链与库版本可能需要修改；使用和复制源码前检查原项目许可证及其依赖许可。

## STM32：HAL、原厂 C 驱动与示例

| 器件 / 功能 | 接口 | 驱动或例程 | 平台与使用提示 |
| --- | --- | --- | --- |
| SSD1306 / SH1106 / SH1107 / SSD1309 OLED | I²C / SPI | [stm32-ssd1306](https://github.com/afiskon/stm32-ssd1306) | STM32 HAL；含 examples，配置控制器、屏幕尺寸和地址 |
| ST7735 彩屏 | SPI | [stm32-st7735](https://github.com/afiskon/stm32-st7735) | STM32 HAL；含 F411 工程，注意屏幕偏移和颜色顺序 |
| ILI9341 彩屏 | SPI | [stm32-ili9341](https://github.com/afiskon/stm32-ili9341) | STM32 显示驱动；按模块修改接线 |
| LCD1602 + I²C 背包 | I²C | [stm32-i2c-lcd-1602](https://github.com/afiskon/stm32-i2c-lcd-1602) | STM32；核对 PCF8574 地址及背包引脚连接 |
| MPU6050 / MPU9250 | I²C / SPI | [STM32-MPU6050-MPU9250-I2C-SPI](https://github.com/MarkSherstan/STM32-MPU6050-MPU9250-I2C-SPI) | STM32 HAL；SPI 仅对应 MPU9250，查看项目示例 |
| DHT11 / AM2301 | 单线时序 | [nimaltd/DHT](https://github.com/nimaltd/DHT) | STM32 HAL；项目使用定时器与 GPIO 中断，GPL-3.0 需核对许可要求 |
| DS18B20 | 1-Wire | [nimaltd/ds18b20](https://github.com/nimaltd/ds18b20) | STM32 HAL；依赖项目的 [1-Wire 库](https://github.com/nimaltd/ow)及定时器，需上拉 |
| HX711 | GPIO 时序 | [nimaltd/HX711](https://github.com/nimaltd/HX711) | STM32 HAL；GPLv2 或商业双授权，称重需去皮和校准 |
| W25Qxx NOR Flash | SPI | [nimaltd/SPIF](https://github.com/nimaltd/SPIF) | STM32 HAL；确认具体芯片和版本依赖，注意擦除与页写 |
| SHT4x | I²C | [Sensirion NUCLEO-F103RB 示例](https://github.com/Sensirion/nucleo-i2c-sht4x) | 厂商例程针对 F103RB 和指定扩展板，其他板卡需改接线和配置 |
| BME280 | I²C / SPI | [Bosch BME280 SensorAPI](https://github.com/boschsensortec/BME280_SensorAPI) | 厂商可移植 C；自行实现 STM32 的读写、延时回调 |
| DS18B20 | 1-Wire | [LibDriver DS18B20](https://github.com/libdriver/ds18b20) | C 驱动，含 STM32F407 项目；按项目接口适配总线时序 |
| ST 运动和环境传感器 | I²C / SPI 等 | [ST MEMS 标准 C 驱动](https://github.com/STMicroelectronics/STMems_Standard_C_drivers) | 原厂传感器驱动集合；选中型号并连接平台读写回调 |

片上 I²C、SPI、定时器等请先参考对应芯片的 [STM32Cube MCU 软件包](https://github.com/STMicroelectronics/STM32Cube_MCU_Overall_Offer)。将第三方驱动接入工程时，核对 HAL 版本、句柄、时钟和 DMA / 中断配置。可用 [awesome-stm32hal](https://github.com/DongHoonPark/awesome-stm32hal) 继续查找；索引项目并不保证逐项验证，需自行检查原仓库。

## ESP32：ESP-IDF 组件与示例

以下乐鑫组件使用 ESP-IDF，不是 Arduino 库。组件的 ESP-IDF 版本和芯片 target 可能不同，应分别查看组件页的依赖、版本和 README；README 中的使用代码不一定是独立的完整示例工程。I²C 新旧驱动及其依赖需匹配。

| 器件 / 功能 | 接口 | 组件或示例 | 说明 |
| --- | --- | --- | --- |
| SSD1306 / SH1107 OLED | I²C | [ESP-IDF I²C OLED 示例](https://github.com/espressif/esp-idf/tree/master/examples/peripherals/lcd/i2c_oled) | ESP-IDF 的显示与 LVGL 示例；按屏和版本配置 |
| AHT20 / AHT30 | I²C | [espressif/aht20](https://components.espressif.com/components/espressif/aht20) | 温湿度；查看组件 README 用法 |
| BME280 | I²C | [espressif/bme280](https://components.espressif.com/components/espressif/bme280) | 温湿度、气压 |
| SHT3x | I²C | [espressif/sht3x](https://components.espressif.com/components/espressif/sht3x) | 温湿度 |
| APDS9960 | I²C | [espressif/apds9960](https://components.espressif.com/components/espressif/apds9960) | 手势、接近与颜色 |
| LIS2DH12 | I²C | [espressif/lis2dh12](https://components.espressif.com/components/espressif/lis2dh12) | 三轴加速度，非六轴 IMU |
| AS5600 | I²C | [espressif/as5600](https://components.espressif.com/components/espressif/as5600/versions/0.1.0/readme) | 磁角度；该版使用 ESP-IDF 5 的新 I²C API |
| AT581x | I²C | [espressif/at581x](https://components.espressif.com/components/espressif/at581x) | 微波雷达检测；按模块与器件资料接线 |
| AT24C02 | I²C | [espressif/at24c02](https://components.espressif.com/components/espressif/at24c02) | EEPROM；检查地址与页写边界 |
| 舵机 | PWM | [espressif/servo](https://components.espressif.com/components/espressif/servo) | PWM 舵机组件及示例；电机单独供电时注意共地 |
| WS2812 灯带 | RMT / SPI | [espressif/led_strip](https://components.espressif.com/components/espressif/led_strip) | 示例与支持接口依具体芯片能力而定 |
| 按键 | GPIO / ADC | [espressif/button](https://components.espressif.com/components/espressif/button) | 按键事件与示例；选对硬件接入方式 |
| 旋转编码器 | GPIO | [espressif/knob](https://components.espressif.com/components/espressif/knob) | 软件解码低速旋钮；高速计数需评估硬件方案 |

其他器件可检索 [ESP-IoT-Solution](https://github.com/espressif/esp-iot-solution) 或 [ESP 组件仓库](https://components.espressif.com/)。社区项目 [esp-idf-lib](https://github.com/esp-idf-lib/core) 已拆分成组件，旧版 [UncleRus/esp-idf-lib](https://github.com/UncleRus/esp-idf-lib) 已归档；选用时核对每个组件的实际版本和许可证。

### 社区 ESP-IDF 组件

下列项目分别提供源码和示例目录，非乐鑫官方组件。先核对每个项目的芯片、ESP-IDF、驱动 API、依赖和许可证，再按 README 安装与配置。

| 器件 / 功能 | 接口 | 项目 | 提示 |
| --- | --- | --- | --- |
| DHT11 / DHT22 | 单线时序 | [esp-idf-lib/dht](https://github.com/esp-idf-lib/dht) | 配置实际引脚、供电及采样间隔 |
| DS18B20 | 1-Wire | [esp-idf-lib/ds18x20](https://github.com/esp-idf-lib/ds18x20) | 检查 1-Wire 依赖与上拉 |
| BH1750 | I²C | [esp-idf-lib/bh1750](https://github.com/esp-idf-lib/bh1750) | 光照，检查 I²C 地址 |
| HC-SR04 | GPIO | [esp-idf-lib/ultrasonic](https://github.com/esp-idf-lib/ultrasonic) | 超声波测距；确认 Echo 电平兼容 ESP32 输入 |
| PCA9685 | I²C | [esp-idf-lib/pca9685](https://github.com/esp-idf-lib/pca9685) | PWM 驱动；舵机供电与逻辑供电分别核对 |
| PCF8574 | I²C | [esp-idf-lib/pcf8574](https://github.com/esp-idf-lib/pcf8574) | GPIO 扩展；不同型号地址范围不同 |
| HD44780 / LCD1602 | 并口或扩展器 | [esp-idf-lib/hd44780](https://github.com/esp-idf-lib/hd44780) | 根据例程选择相应连接方式 |
| BMP280 / BME280 | I²C | [esp-idf-lib/bmp280](https://github.com/esp-idf-lib/bmp280) | 压力与温度；仅 BME280 含湿度 |

## 上手顺序

1. 记录主控具体型号、开发框架版本、模块芯片、供电和接口；先找同平台、同器件的例程。
2. 检查原项目 README、示例、许可证及依赖；准备对应开发环境，核对引脚与电平。
3. 先验证总线和读设备 ID，或让屏幕显示简单图形；再加入完整应用。遇到时序型器件要核对定时器、时钟及中断。
4. 记录实测结果、软件版本及接线。链接存在或代码可编译，都不等于已在具体硬件上正常工作。
