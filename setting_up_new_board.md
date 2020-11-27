Adafruit has great documentation about setting the board up [here](https://learn.adafruit.com/adafruit-magtag/rom-bootloader). 
These are my notes for my environment. 

#### Enter ROM Bootloader Mode
1. Press and hold boot0 button
2. Press and release reboot button
3. Release boot0 button
4. Check for new serial/COM port
  - mine shows as /dev/ttyACMO
5. Upgrade esptool
  ````pip install --upgrade esptool````
6. Add myself to tty and dialout usergroups
- ````sudo usermod -a -G tty uid````
- ````sudo usermod -a -G dialout uid````
- logout/login
7. Run esptool
  ````esptool.py --port ttyACM0 chip_id````
