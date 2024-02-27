# pi-top [4] Display Port

This package manages kernel modules, udev rules and system configuration (such as a DHCP server) to allow plug-and-play network connections (such as SSH and VNC) with a pi-top [4] via its USB-OTG connection from the Raspberry Pi's USB-C port.

Configures Raspberry Pi 4's USB-OTG port as a virtual Ethernet interface called `ptusb0` with a Mac address of `00:11:22:33:44:55`.

This package works by configuring the `isc-dhcp-server` (on `bullseye`) or `NetworkManager` (on `bookworm`) service to run a few commands on startup. It configures a DHCP server on the `ptusb0` interface to assign IP addresses to other devices, so that they can connect via plug-and-play.