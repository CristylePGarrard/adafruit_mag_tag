Adafruit has great documentation about setting the board up [here](https://learn.adafruit.com/adafruit-magtag/rom-bootloader). 
These are my notes for my environment. 

#### Enter ROM Bootloader Mode
1. Upgrade esptool
  ````pip install --upgrade esptool````
2. Add myself to tty and dialout usergroups
- ````sudo usermod -a -G tty uid````
- ````sudo usermod -a -G dialout uid````
- logout/login
3. Press and hold boot0 button
4. Press and release reboot button
5. Release boot0 button
6. Check for new serial/COM port
  - mine shows as /dev/ttyACMO
7. Run esptool
  ````esptool.py --port /dev/ttyACM0 chip_id````
  output
  ```esptool.py v3.0
Serial port /dev/ttyACM0
Connecting....
Detecting chip type... ESP32-S2
Chip is ESP32-S2
Features: WiFi, ADC and temperature sensor calibration in BLK2 of efuse
Crystal is 40MHz
MAC: 7c:df:a1:06:88:3c
Uploading stub...
Running stub...
Stub running...
Warning: ESP32-S2 has no Chip ID. Reading MAC instead.
MAC: 7c:df:a1:06:88:3c
Hard resetting via RTS pin...
ERROR: ESP32-S2 chip was placed into download mode using GPIO0.
esptool.py can not exit the download mode over USB. To run the app, reset the chip manually.
To suppress this error, set --after option to 'no_reset'.
```
8. Download CircuitPython .bin file from [here](https://circuitpython.org/board/adafruit_magtag_2.9_grayscale/)
9. upload binary file
```esptool.py --port /dev/ttyACM0 --after=no_reset write_flash 0x0 Downloads/adafruit-circuitpython-adafruit_magtag_2.9_grayscale-en_US-6.1.0-beta.1.bin```
output
```
esptool.py v3.0
Serial port /dev/ttyACM0
Connecting...
Detecting chip type... ESP32-S2
Chip is ESP32-S2
Features: WiFi, ADC and temperature sensor calibration in BLK2 of efuse
Crystal is 40MHz
MAC: 7c:df:a1:06:88:3c
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Compressed 1315680 bytes to 849813...
Wrote 1315680 bytes (849813 compressed) at 0x00000000 in 14.6 seconds (effective 721.0 kbit/s)...
Hash of data verified.

Leaving...
Staying in bootloader.
```
