# Virtual Firewall Installation Guide using OPNsense

This guide provides step-by-step instructions on how to set up a virtual firewall using OPNsense on a virtual machine.

## Prerequisites

- VirtualBox
- Internet connection to download OPNsense
- Basic knowledge of virtual machine creation and networking

## Installation Steps

### Download OPNsense

1. Download OPNsense ISO from the official [download page](https://opnsense.org/download/).
2. Verify the SHA-256 hash of the downloaded ISO to ensure its integrity.
3. Extract the ISO file if necessary.

### Create a New Virtual Machine

1. Select the operating system as FreeBSD (64-bit).
2. Allocate at least 2GB of RAM.
3. Assign 2 CPU cores.
4. Create a virtual hard disk with at least 8GB of storage.

### Configure Network Adapters

1. Set up the first network adapter to use NAT (this will act as the WAN interface).
2. Set up the second network adapter to use NAT Network (this will serve as the switch for the LAN).

### Initial Installation

1. Start the virtual machine with the OPNsense ISO mounted.
2. Log in with the following credentials:
   - Username: `installer`
   - Password: `opnsense`
3. Follow the prompts to install OPNsense using UFS.
4. Select the virtual hard disk you created earlier to install OPNsense.
5. After installation, change the root password as prompted.

### Post-Installation Setup

1. Remove the ISO from the virtual machine's optical drive.
2. Reboot the machine to start OPNsense from the hard disk.

### OPNsense Configuration

1. Log in to OPNsense using the root account and the password you set during installation.
2. When prompted, assign network interfaces:
   - WAN interface name: `em0`
   - LAN interface name: `em1`
3. Set the LAN interface IP address to `10.200.200.254` with a subnet mask of `255.255.255.0`.
4. Decline to configure IPv6 settings and DHCP server for now.

### Accessing the Web Interface

1. From a Kali Linux VM, configure the network interface with a static IP `10.200.200.10`.
2. Ping the OPNsense firewall to ensure connectivity.
3. Access the OPNsense web portal via a web browser.

### Updating OPNsense

1. In the OPNsense web interface, navigate to "Firmware", then to "Status" and check for updates.
2. Install any available updates.
3. Go to "Plugins" and install the OS-VirtualBox Extension if available.

## Conclusion

Following these steps will set up OPNsense as a virtual firewall with basic configurations. Further customization and security settings are recommended based on your specific network requirements.

## Support

For issues, questions, or contributions, please open an issue or pull request in this repository.
