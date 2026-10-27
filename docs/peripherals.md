# 显示、通信与其他外设

[返回首页](../README.md) · [传感器](sensors.md)

资料指向原始开源项目，实际支持的芯片、开发板、接口和许可证请以项目文档为准。表格中的平台是使用入口，不代表可以直接复制到任意 MCU 工程。

## OLED、LCD 与图形界面

| 器件 / 方向 | 开源资料 | 平台和用途 |
| --- | --- | --- |
| SSD1306、SH1106、ST7920 等单色屏 | [U8g2](https://github.com/olikraus/u8g2) | Arduino 和可移植 C；支持多种 OLED/LCD 控制器，STM32 等需要适配底层接口 |
| SSD1306 OLED | [Adafruit SSD1306](https://github.com/adafruit/Adafruit_SSD1306) | Arduino，I²C/SPI；依赖 Adafruit GFX |
| ST7735、ST7789、ILI9341、GC9A01 等 TFT | [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) | Arduino / ESP32、ESP8266、RP2040 等；按屏幕和板卡配置引脚与驱动 |
| 图形用户界面 | [LVGL](https://github.com/lvgl/lvgl) · [文档](https://docs.lvgl.io/) | 跨平台 UI 框架；需要显示和输入设备驱动，不是单一屏幕驱动 |
| 电子墨水屏 | [GxEPD2](https://github.com/ZinggJM/GxEPD2) | Arduino；确认屏幕控制器和电压 |
| XPT2046 电阻触摸 | [XPT2046 Touchscreen](https://github.com/PaulStoffregen/XPT2046_Touchscreen) | Arduino / SPI；需对坐标进行校准 |

## 无线、射频与识别

| 器件 / 方向 | 开源资料 | 平台和用途 |
| --- | --- | --- |
| SX126x / SX127x、CC1101 等 | [RadioLib](https://github.com/jgromes/RadioLib) | Arduino 和嵌入式无线收发；具体器件看支持列表 |
| nRF24L01+ | [RF24](https://github.com/nRF24/RF24) | Arduino、Pico SDK、Linux 等；2.4 GHz 收发，需检查供电 |
| PN532 | [Adafruit PN532](https://github.com/adafruit/Adafruit-PN532) | Arduino；NFC，支持具体库列出的 I²C/SPI 模式 |
| MFRC522 | [MFRC522 RFID](https://github.com/miguelbalboa/rfid) | Arduino / SPI；项目维护有限，UID 不适合作为安全认证凭据 |
| ESP32 / ESP8266 红外遥控 | [IRremoteESP8266](https://github.com/crankyoldgit/IRremoteESP8266) | Arduino；红外协议的发送与接收 |
| ESP Wi-Fi | [ESP-IDF Wi-Fi 示例](https://github.com/espressif/esp-idf/tree/master/examples/wifi) | ESP-IDF；按具体芯片支持情况使用 |
| ESP AT 模组 | [ESP-AT](https://github.com/espressif/esp-at) | 外部主控通过 AT 命令使用乐鑫模组；确认固件和芯片支持表 |
| BLE | [NimBLE-Arduino](https://github.com/h2zero/NimBLE-Arduino) | Arduino；支持 ESP32、nRF 等具体平台，BLE 而非经典蓝牙 |

## 有线通信与接口扩展

| 器件 / 方向 | 开源资料 | 平台和用途 |
| --- | --- | --- |
| W5100 / W5200 / W5500 以太网 | [Arduino Ethernet](https://github.com/arduino-libraries/Ethernet) | Arduino / SPI；检查芯片与板卡支持 |
| MCP2515 CAN 控制器 | [MCP_CAN_lib](https://github.com/coryjfowler/MCP_CAN_lib) | Arduino / SPI；连接 CAN 总线还需要收发器和正确终端电阻 |
| Modbus RTU / TCP | [modbus-esp8266](https://github.com/emelianov/modbus-esp8266) | Arduino；具体平台和传输方式见项目，RS-485 需要收发器 |
| MCP23008 / MCP23017 GPIO 扩展 | [Adafruit MCP23017](https://github.com/adafruit/Adafruit-MCP23017-Arduino-Library) | Arduino / I²C；项目也支持部分 SPI 型号 |
| ADS1015 / ADS1115 ADC | [Adafruit ADS1X15](https://github.com/adafruit/Adafruit_ADS1X15) | Arduino / I²C；输入范围和供电限制以数据手册为准 |
| MCP4725 DAC | [Adafruit MCP4725](https://github.com/adafruit/Adafruit_MCP4725) | Arduino / I²C，12 位 DAC |
| DS3231 / DS1307 等实时时钟 | [RTClib](https://github.com/adafruit/RTClib) | Arduino / I²C；断电计时需正确安装后备电源 |

## 存储与文件系统

| 器件 / 方向 | 开源资料 | 平台和用途 |
| --- | --- | --- |
| SD / microSD 卡 | [SdFat](https://github.com/greiman/SdFat) | Arduino；SD 卡 FAT16、FAT32、exFAT |
| 嵌入式 Flash 文件系统 | [littlefs](https://github.com/littlefs-project/littlefs) | C；需实现块设备接口，面向嵌入式及断电恢复场景 |
| 24LC 系列 EEPROM | [I2C_EEPROM](https://github.com/RobTillaart/I2C_EEPROM) | Arduino / I²C；注意容量、页写边界和写入周期 |

## 按键、灯光、音频与摄像头

| 器件 / 方向 | 开源资料 | 平台和用途 |
| --- | --- | --- |
| 按键 | [OneButton](https://github.com/mathertel/OneButton) | Arduino；消抖、单击、双击、长按 |
| WS2812 等可寻址灯带 | [FastLED](https://github.com/FastLED/FastLED) | Arduino / ESP32 等；注意具体芯片、时序和电源 |
| OV2640、OV5640 等摄像头 | [esp32-camera](https://github.com/espressif/esp32-camera) | ESP32 系列；传感器与芯片支持范围查项目说明 |
| 音频开发 | [ESP-ADF](https://github.com/espressif/esp-adf) | ESP32 系列音频框架；需要相应硬件及 ESP-IDF 版本 |

## 电机与执行器

| 器件 / 方向 | 开源资料 | 平台和用途 |
| --- | --- | --- |
| BLDC / 步进电机 FOC | [SimpleFOC](https://github.com/simplefoc/Arduino-FOC) | Arduino 生态多平台；配合电机驱动、电源和必要的传感器 |
| STEP / DIR 步进驱动器 | [FastAccelStepper](https://github.com/gin66/FastAccelStepper) | Arduino 多平台；步进脉冲及加减速，支持范围依板卡而异 |
| ESP 舵机 / 电机组件 | [ESP-IoT-Solution](https://github.com/espressif/esp-iot-solution) | ESP-IDF；按实际组件和型号选择 |
