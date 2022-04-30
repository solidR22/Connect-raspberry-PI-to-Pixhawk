# Hardware:
connect Raspberry Pi to Pixhawk by USB

# Software:
## PixHawk
Burned into the ArduPilot firmware

## Raspberry Pi
### Terminal
install **mavproxy** and **pymavlink**
``` shell
sudo pip3 install mavproxy
sudo pip3 install pymavlink
```
after installation
```shell
sudo mavproxy.py --master=/dev/ttyACM0 --out=udp:0.0.0.0:14660
```
### Then run the following python Program
 ```python
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpin:0.0.0.0:14660')
master.wait_heartbeat()
print("Heartbeat from system (system %u component %u)" % ( \
            master.target_system, master.target_system))
```
you have done it if print successfully!

# Note
1.Using series connect to pixhawk directly would cause interruped often.

2.The following program can connect pixhawk to QGC, but the connection to Raspberry Pi would fail.
```shell
sudo mavproxy.py --master=/dev/ttyACM0 --out=udp:(ip of computer):14660
```
