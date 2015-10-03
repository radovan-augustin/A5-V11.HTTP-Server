
A5-V11.HTTP-Server is set of files of specific firmware for A5-V11 board (2.)

Features:
  - Minimalistic OpenWrt configuration:
    - without hotplug, udev, luci and other components
    - with drivers for TCP/IPv4 and USB mass storage
    - without libstdc++
    - with uClibc++
  - nginx 1.9.5:
    - reads configuration and HTTP response data from USB attached storage
    - writes pid, access and error logs to /tmp
  - Telnet access

Default firmware configuration:
  - No overlay fs
  - No root password
  - Network interface configured as static with IP 192.168.1.1
  - USB attached storage mounted to /usbstorage as type vfat, with options noatime, nodiratime, ro

How to compile firmware:
  - Export trunk OpenWrt
  - Copy files from A5-V11.HTTP-Server into directory with OpenWrt
  - Run make

Links:
1. https://www.openwrt.org/
2. http://wiki.openwrt.org/toh/unbranded/a5-v11
3. http://nginx.org/
