# pi-top [4] Display Port

This package manages kernel modules, udev rules and system configuration (such as a DHCP server) to allow plug-and-play network connections (such as SSH and VNC) with a pi-top [4] via its USB-OTG connection from the Raspberry Pi's USB-C port.

Configures Raspberry Pi 4's USB-OTG port as a virtual Ethernet interface called `ptusb0` with a Mac address of `00:11:22:33:44:55`.

This package works by configuring the `isc-dhcp-server` service to run a few commands before starting:
```
/usr/bin/raspi-config nonint is_pifour
/usr/lib/pt-display-port/ptusb0/setup/ptusb0-setup
/usr/lib/pt-display-port/dhcp-server/setup/dhcp-server-setup
/bin/sleep 2
```

This means that when the DHCP service is started, it serves on the `ptusb0` interface in order to assign IP addresses to other devices, so that they can connect via plug-and-play.
