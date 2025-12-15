## 测试命令
### 硬件测试命令

#### 🎨RGB 测试
cd /sys/class/leds/rgb\:red

echo 255 > ./brightness

echo 0 > ./brightness

#### 🎨数码管LEDs 测试
cd /sys/class/leds/badge\:matrix\:led1_a/ #led1_a 到led2_g

echo 1 > ./brightness

echo 0 > ./brightness

#### 🎨按键 测试
evtest /dev/input/event0

#### 🎨ADC 测试
cd /sys/bus/iio/devices/iio\:device2    # 光照

cat ./in_voltage2_raw                   # mikrobus

cat ./in_voltage1_raw

#### 🎨Buzzer 测试
cd /sys/class/pwm/pwmchip1/

echo 0 > ./export

echo 1000000 > pwm0/period

echo 500000 > pwm0/duty_cycle

echo 1 > pwm0/enable

echo 0 > pwm0/enable

#### 🎨ePaper 测试
cd /mnt/

./epaper_test

./epaper_test_boy

#### 🎨LoRa 测试
cd /mnt

./sx126x_demo

#### 🎨IMU 测试
cd /sys/bus/iio/devices/iio\:device1

cat in_accel_x_raw in_accel_y_raw in_accel_z_raw

#### 🎨电量计 测试
##### 读取电池电压
i2cget -y 1 0x55 0x08 w

##### 读取剩余容量
i2cget -y 1 0x55 0x10 w

##### 读取电池电流
i2cget -y 1 0x55 0x14 w

#### 🎨Grove UART 测试
##### UART
minicom -D /dev/ttyS5 -b 9600

#### 🎨mikroBUS 测试
##### UART
minicom -D /dev/ttyS4 -b 9600
##### ADC
cd /sys/bus/iio/devices/iio\:device2

cat ./in_voltage1_raw

##### PWM
cd /sys/class/pwm/pwmchip0/

echo 0 > ./export

echo 1000000 > pwm0/period

echo 500000 > pwm0/duty_cycle

echo 1 > pwm0/enable

echo 0 > pwm0/enable

##### GPIO
cd /sys/class/gpio/
echo 603 > ./export
echo out > ./gpio603/direction
echo 1 > ./gpio603/value

#### 🎨QWIIC 测试
##### J6
i2cdetect  -r -y 2

##### J7
i2cdetect  -r -y 3


#### 🎨EEPROM 测试
cd /sys/class/i2c-dev/i2c-1/device/1-0050

cat eeprom | hexdump -C

echo hh > ./eeprom

dmesg | grep -i eeprom

#### 🎨OSPI 测速
##### 读测试
dd if=/dev/mtdblock5 of=/tmp/test_file bs=1M count=10 oflag=direct
##### 写测试
dd if=/dev/zero of=/dev/mtdblock5 bs=1M count=10 oflag=direct

#### 🎨GPIO 测试
./test_gpio.sh 0

./test_gpio.sh 1

