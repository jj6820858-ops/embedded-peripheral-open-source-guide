# 传感器与测量模块

[返回首页](../README.md) · [其他外设](peripherals.md)

表中链接指向原始项目；请打开项目的 README 和 examples 查看接线、依赖、示例、支持器件与许可证。Arduino 库依赖 Arduino 生态；标注可移植 C 的驱动仍需适配底层总线和延时。相同模块名称可能搭配不同芯片。

## 温湿度与气压

| 器件 | 测量内容 / 接口 | 开源资料 | 平台与提示 |
| --- | --- | --- | --- |
| DHT11 / DHT22 / AM2302 | 温湿度 / 单线时序 | [Adafruit DHT sensor library](https://github.com/adafruit/DHT-sensor-library) | Arduino；注意供电和采样间隔 |
| DS18B20 | 温度 / 1-Wire | [DallasTemperature](https://github.com/milesburton/Arduino-Temperature-Control-Library) | Arduino；需要 OneWire 库和上拉 |
| SHT31 | 温湿度 / I²C | [Adafruit SHT31](https://github.com/adafruit/Adafruit_SHT31) | Arduino |
| BME280 | 温湿度、气压 / I²C、SPI | [Bosch BME280 SensorAPI](https://github.com/boschsensortec/BME280_SensorAPI) | 可移植 C；适配总线回调 |
| BME680 / BME688 | 温湿度、气压、气体电阻 / I²C、SPI | [Bosch BME68x SensorAPI](https://github.com/boschsensortec/BME68x_SensorAPI) | 可移植 C；气体电阻不等同于 CO₂ 浓度 |
| BMP280 | 温度、气压 / I²C、SPI | [Adafruit BMP280](https://github.com/adafruit/Adafruit_BMP280_Library) | Arduino；BMP280 不测湿度 |
| MLX90614 | 非接触红外温度 / I²C、SMBus | [Adafruit MLX90614](https://github.com/adafruit/Adafruit-MLX90614-Library) | Arduino；读数受发射率和环境影响 |
| MLX90640 | 红外热成像 / I²C | [Adafruit MLX90640](https://github.com/adafruit/Adafruit_MLX90640) | Arduino；注意内存及总线速率要求 |
| AHT10 / AHT20 | 温湿度 / I²C | [Arduino AHTX0](https://github.com/adafruit/Adafruit_AHTX0) · [CircuitPython AHTx0](https://github.com/adafruit/Adafruit_CircuitPython_AHTx0) | Arduino / CircuitPython 分别选库；不能假定与 MicroPython 兼容 |
| SHT4x | 温湿度 / I²C | [Sensirion Arduino SHT4x](https://github.com/Sensirion/arduino-i2c-sht4x) | Arduino；厂商示例 |
| BMP388 / BMP390 | 气压、温度 / I²C、SPI | [Adafruit BMP3XX](https://github.com/adafruit/Adafruit_BMP3XX) | Arduino |
| MAX31865 + PT100 / PT1000 | 热电阻温度接口 / SPI | [Adafruit MAX31865](https://github.com/adafruit/Adafruit_MAX31865) | Arduino；配置二、三、四线及参考电阻；不是热电偶接口 |
| MAX31855 + 热电偶 | 热电偶温度接口 / SPI | [MAX31855](https://github.com/Zanduino/MAX31855) | Arduino；核对芯片支持的热电偶类型及电平 |

## 运动、姿态与磁场

| 器件 | 测量内容 / 接口 | 开源资料 | 平台与提示 |
| --- | --- | --- | --- |
| MPU6050 等 | 加速度、角速度 / I²C | [I2Cdevlib](https://github.com/jrowberg/i2cdevlib) | Arduino / C++ 为主；集合中不同器件适配不同 |
| BMI270 | 加速度、角速度 / I²C、SPI | [Bosch BMI270 SensorAPI](https://github.com/boschsensortec/BMI270_SensorAPI) | 可移植 C；参照示例完成初始化 |
| BNO055 | 姿态融合、加速度等 | [Bosch BNO055 SensorAPI](https://github.com/boschsensortec/BNO055_SensorAPI) | C；对照具体模块接线及通信配置 |
| ST 系列 MEMS | 加速度、陀螺仪、磁场等 | [ST MEMS 标准 C 驱动](https://github.com/STMicroelectronics/STMems_Standard_C_drivers) | 可移植 C；按具体型号查找 |
| MPU6050 | 加速度、角速度 / I²C | [Adafruit MPU6050](https://github.com/adafruit/Adafruit_MPU6050) | Arduino |
| ADXL345 | 加速度 / I²C、SPI | [Adafruit ADXL345](https://github.com/adafruit/Adafruit_ADXL345) | Arduino |
| HMC5883L | 磁场 / I²C | [Adafruit HMC5883](https://github.com/adafruit/Adafruit_HMC5883_Unified) | Arduino；确认芯片并校准磁场 |
| QMC5883L | 磁场 / I²C | [QMC5883LCompass](https://github.com/mprograms/QMC5883LCompass) | Arduino；与 HMC5883L 不可混用驱动 |
| LIS3MDL | 磁场 / I²C、SPI | [Adafruit LIS3MDL](https://github.com/adafruit/Adafruit_LIS3MDL) | Arduino |
| AS5600 | 磁角度 / I²C | [AS5600](https://github.com/RobTillaart/AS5600) | Arduino；注意磁铁安装和校准 |
| LSM6DS3 | 加速度、角速度 / I²C、SPI | [STM32duino LSM6DS3](https://github.com/stm32duino/LSM6DS3) | STM32duino / Arduino；按模块检查引脚 |
| LSM6DSOX 等 | 加速度、角速度 / I²C、SPI | [Adafruit LSM6DS](https://github.com/adafruit/Adafruit_LSM6DS) | Arduino；核对库中实际支持型号 |
| 姿态融合 | IMU 数据处理 | [Adafruit AHRS](https://github.com/adafruit/Adafruit_AHRS) | Arduino；Madgwick / Mahony 算法，磁力计需校准 |

## 距离、光学与颜色

| 器件 | 测量内容 / 接口 | 开源资料 | 平台与提示 |
| --- | --- | --- | --- |
| VL53L0X | ToF 距离 / I²C | [Pololu VL53L0X](https://github.com/pololu/vl53l0x-arduino) | Arduino |
| VL53L1X | ToF 距离 / I²C | [Pololu VL53L1X](https://github.com/pololu/vl53l1x-arduino) | Arduino；不要与 VL53L0X 驱动混用 |
| TCS34725 | 颜色 / I²C | [Adafruit TCS34725](https://github.com/adafruit/Adafruit_TCS34725) | Arduino；读数受照明影响 |
| MAX30102 / MAX30105 | 光电信号 / I²C | [SparkFun MAX3010x](https://github.com/sparkfun/SparkFun_MAX3010x_Sensor_Library) | Arduino；示例输出不构成医疗诊断 |
| HC-SR04 | 超声波测距 / TRIG、ECHO | [arduino-lib-hc-sr04](https://github.com/Martinsos/arduino-lib-hc-sr04) | Arduino；检查 Echo 电平与主控兼容性 |
| BH1750 | 环境光照 / I²C | [BH1750](https://github.com/claws/BH1750) | Arduino |
| TSL2591 | 环境光照 / I²C | [Adafruit TSL2591](https://github.com/adafruit/Adafruit_TSL2591_Library) | Arduino |
| APDS9960 | 手势、接近、颜色 / I²C | [Adafruit APDS9960](https://github.com/adafruit/Adafruit_APDS9960) | Arduino；受环境光与遮挡影响 |
| XM125 | 雷达测距、存在检测 / I²C | [SparkFun Qwiic XM125](https://github.com/sparkfun/SparkFun_Qwiic_XM125_Arduino_Library) | Arduino；按用途选择与配置对应模块固件 |
| LD2410 | 毫米波人体存在检测 / UART | [ld2410](https://github.com/ncmreynolds/ld2410) | Arduino；注意串口波特率、供电和电平 |
| VEML6075 | UVA / UVB / I²C | [Adafruit VEML6075](https://github.com/adafruit/Adafruit_CircuitPython_VEML6075) | CircuitPython；确认运行时兼容性 |

## 气体、颗粒物与重量

| 器件 | 测量内容 / 接口 | 开源资料 | 平台与提示 |
| --- | --- | --- | --- |
| SCD4x | CO₂、温湿度 / I²C | [Sensirion SCD4x](https://github.com/Sensirion/arduino-i2c-scd4x) | Arduino；注意通风与校准 |
| SPS30 | 颗粒物 / I²C | [Sensirion SPS30](https://github.com/Sensirion/arduino-i2c-sps30) | Arduino；具体模块也可能支持其他接口 |
| Grove 多气体模块 | 气体测量 | [Seeed Arduino MultiGas](https://github.com/Seeed-Studio/Seeed_Arduino_MultiGas) | Arduino；确认对应 Grove 硬件版本 |
| HX711 | 称重桥式传感器 ADC / GPIO 时序 | [bogde/HX711](https://github.com/bogde/HX711) | Arduino；需去皮和标定，HX711 本身不是称重传感器 |
| SGP30 | 空气质量 / I²C | [SparkFun SGP30](https://github.com/sparkfun/SparkFun_SGP30_Arduino_Library) | Arduino；eCO₂ 是估算值 |
| SCD30 | CO₂、温湿度 / I²C | [Sensirion Arduino SCD30](https://github.com/Sensirion/arduino-i2c-scd30) | Arduino；根据应用检查校准条件 |
| SEN5x | 环境综合监测 / I²C | [Sensirion Arduino SEN5x](https://github.com/Sensirion/arduino-i2c-sen5x) | Arduino；具体测量功能依型号而定 |
| SDP 系列 | 差压 / I²C | [Sensirion Arduino SDP](https://github.com/Sensirion/arduino-i2c-sdp) | Arduino；选择对应型号及量程 |
| PMS5003 | 颗粒物 / UART | [PMS5003 Arduino 库](https://github.com/jbanaszczyk/pms5003) | Arduino；检查供电及串口电平 |
| DFRobot pH 模块 V2 | pH 测量 / 模拟量 | [DFRobot pH](https://github.com/DFRobot/DFRobot_PH) | Arduino；按说明用标准缓冲液标定，并核对板卡兼容性 |

## 电源测量与定位

| 器件 | 测量内容 / 接口 | 开源资料 | 平台与提示 |
| --- | --- | --- | --- |
| INA219 | 电流、电压、功率 / I²C | [Adafruit INA219](https://github.com/adafruit/Adafruit_INA219) | Arduino；注意量程和分流电阻 |
| INA226 | 电流、电压、功率 / I²C | [INA226](https://github.com/RobTillaart/INA226) | Arduino；配置实际分流电阻 |
| INA260 | 电流、电压、功率 / I²C | [Adafruit INA260](https://github.com/adafruit/Adafruit_INA260) | Arduino；量程与接线以芯片手册为准 |
| MAX17048 / MAX17049 | 电池电量计 / I²C | [Adafruit MAX1704X](https://github.com/adafruit/Adafruit_MAX1704X) | Arduino；确认电池串数、芯片和板卡供电方式 |
| 通用 GNSS NMEA | 定位数据解析 / 常用 UART | [TinyGPSPlus](https://github.com/mikalhart/TinyGPSPlus) | Arduino；是 NMEA 解析库，需要接收机输出 |
| u-blox GNSS | 定位 / UART、I²C、SPI 等 | [SparkFun u-blox GNSS](https://github.com/sparkfun/SparkFun_u-blox_GNSS_Arduino_Library) | Arduino；具体接口依模块而定 |

## 厂商驱动集合与可移植 C

| 资源 | 用途 | 平台与提示 |
| --- | --- | --- |
| [Sensirion 驱动索引](https://github.com/Sensirion/info) | SHT、SCD、SPS、SGP、SDP 等型号驱动入口 | 包括嵌入式 C、Arduino 等；按器件与总线选择 |
| [SCD4x 嵌入式 C 驱动](https://github.com/Sensirion/embedded-i2c-scd4x) | SCD4x CO₂ 传感器 / I²C | 移植到 MCU 时需实现 I²C HAL、延时及相关配置 |
| [SHT4x 嵌入式 C 驱动](https://github.com/Sensirion/embedded-i2c-sht4x) | SHT4x 温湿度 / I²C | 实现 I²C 和延时 HAL |
| [SGP40 嵌入式 C 驱动](https://github.com/Sensirion/embedded-i2c-sgp40) | SGP40 VOC 传感器 / I²C | 实现 I²C 和延时 HAL；按项目说明处理算法 |
| [SPS 嵌入式 UART 驱动](https://github.com/Sensirion/embedded-uart-sps) | SPS 系列颗粒物 / UART | 根据模块和例程配置 UART 与延时 |
| [Bosch BMP3 SensorAPI](https://github.com/boschsensortec/BMP3_SensorAPI) | BMP3 系列气压 / I²C、SPI | C 驱动；根据接口对接回调 |
| [Bosch SensorAPI 驱动索引](https://www.bosch-sensortec.com/en/software-tools/software/drivers/) | 查找 Bosch 环境、运动及磁场传感器 | 选择具体型号，核对对应源码许可证与移植接口 |

土壤湿度、人体感应、漏水等简单 ADC / GPIO 模块另见[常见模拟量与开关量模块](basic-modules.md)。
