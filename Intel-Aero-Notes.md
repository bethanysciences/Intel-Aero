
Latest Software (BIOS & OS image) BSP Released v01.00.04 on 12/20/2016 
 
Aero SSID: CR-AP-A0C589095FBF
$ ls /dev/cu.*
$ screen /dev/cu. 115200 –L 
$ ctrl a ctrl \ to end ps | kill // finds terminal sessions 
--------------------------------------- 
## USB ssh  
* power up Aero Board  
* disable host networking 
* assign host IP address to usb0: sudo ifconfig usb0 192.168.7.1  
* Aero IP for usb interface is 192.168.7.2  
'''
ssh root@192.168.7.2  
''' 
---------------------------------------
# Update BIOS 
1. [QuickStart](https://github.com/intel-aero/meta-intel-aero/wiki/Quickstart-Guide)   
2. [Download BIOS image](https://downloadcenter.intel.com/download/26500/UAV-installation-files-for-Intel-Aero-Platform)  
3. Verify new BIOS image md5sum
4. copy rpm file into root
'''
$ root@intel-aero:~# mkdir temp  
$ root@intel-aero:~# mount -t vfat /dev/sda1 ~/temp  
$ root@intel-aero:~# rpm -ivh capsule-01.00.12-r0.core2_64  
'''
Message indicates rpm successfully installed in /boot/  
Preparing...                  ############################################ [100%]  
    1. capsule                ############################################ [100%]   
'''
$ Reboot  
'''
-----------------------------------------  
## Update FPGA Firmware  
'''  
$ root@intel-aero:~# cd /etc  
$ root@intel-aero:~# jam -aprogram aero_RTF_kit_fpga.jam  
'''  
-----------------------------------------  
## Update Dronecode PX4 firmware  
'''  
root@intel-aero:~# cd /etc/px4-fw  
root@intel-aero:~# aerofc_update.sh nuttx-aerofc-v1-default.px4  
'''  
-----------------------------------------  
## Specifications  
- Battery: Li-Po 4S 4000mAh+ (XT60 connector)  
- [QGroundControl](http://qgroundcontrol.com/)  
– Voltage Input 11.1 - 14.8V  
– Intel Aero Compute Board  
	** Intel® AtomTM x7-Z8750 processor  
	** 4 GB LPDDR3-1600  
	** 32 GB eMMC  
	** Dual Band Wireless-AC 8260  
	** MicroSD slot  
	** M.2 connector 1 lane PCIe for SSD  
	** USB 3.0 OTG  
	** Reprogrammable I/O via Altera Max 10 FPGA  
	** Insyde Software InsydeH2O UEFI BIOS optimized for Aero Platform  
– Dronecode PX4 autopilot (STM32 MCU, MAVLink protocol over HSUART)  
- Sensors
	** Intel RealSense camera (R200)  
	** 8MP RGB camera (front-facing)  
	** down-facing monochrome VGA camera w/ global shutter
	** 6 degrees of freedom (DoF) inertial measurement unit (IMU)
	** magnetometer
	** altitude
	** GPS and compass
- Props Yuneec Typhoon H 230mm
	[A type](http://shop.yuneecusa.com/typhoon-h-propeller-a)  
	[B type](http://shop.yuneecusa.com/typhoon-h-propeller-b)
– [Yuneec Typhoon H motors](https://www.vertigodrones.com/Yuneec-Replacement-Motor-Typhoon-H_p_344.html)
- Yuneec Typhoon H electronic speed controllers
– [Spektrum* DSMX* Serial Receiver](https://www.spektrumrc.com/Products/Default.aspx?ProdID=SPM4648)
– [Spektrum DXe Transmitter (2.4GHz DSMX)](https://www.spektrumrc.com/Products/Default.aspx?ProdId=SPM1000)
– Flight time: 20 min (4S 4000mAh battery, hovering, no added payload)  
– Max sustained wind: 15 knots
– Max control range: 300m
– Max airspeed: 15 m/s
– Max operational altitude: 5000msl
– Temperature range (min / max): -0 C / +45 C
– Weight without battery: 865g  
– Max takeoff gross weight: 1900g 
– Width: 360 mm (hub-to-hub)
– Height: 222 mm (base to top of GPS antenna)
