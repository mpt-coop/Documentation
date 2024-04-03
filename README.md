# MPT - A multiplayer mod for SPT

<details>
	<summary>Table of Contents</summary>
	<ol>
		<li><a href="#what-is-mpt">What is MPT</a></li>
		<li><a href="#license">License</a></li>
		<li>
           	<a href="#prerequisites">Prerequisites</a>
            <ul>
                <li><a href="#hosting">Hosting</a></li>
                <li><a href="#client">Client</a></li>
            </ul>
        </li>
        <li><a href="#hardware-requirements">Hardware Requirements</a></li>
		<li>
	            <a href="#installation">Installation</a>
	            <ul>
	                <li><a href="#host-using-port-forwarding">Host using port forwarding</a></li>
	                <li><a href="#host-using-a-vpn">Host using a VPN</a></li>
	                <li><a href="#client-using-port-forwarding">Client using port forwarding</a></li>
	                <li><a href="#client-using-a-vpn">Client using a VPN</a></li>
	            </ul>
	        </li>
		<li><a href="#credits">Credits</a></li>
	</ol>
</details>

## What is MPT

**MPT** is a mod for **SPT-Aki** that allows you to play COOP with your friends. It utilizes a P2P-UDP connection for a modern and performant experience. The main goals of MPT are: performance, accuracy and mod-support. MPT is currently maintained by the MPT team.

## License

<img src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-nc-nd.png" alt="cc by-nc-nd" width="196" height="62" style="float:right">

This project is licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode.en).

- You may only share MPT as long as proper credits are given, it is not used for commercial purposes and you do not modify it
- You may not monetize your server in terms of payments or donations.
- You may not host massive public servers, MPT is meant for COOP with your friends.
- You may not copy and/or replicate the code by MPT, nor may you use its assets that are handcrafted by our developers and artists.

## Prerequisites

MPT requires general knowledge of computers, networking and Aki. If you are not comfortable with these concepts, this project is not for you. Please try to understand and respect this.

### Hosting

- Router and ISP that supports either **Port Forwarding** or **UPnP**
- A router that supports NAT Loopback if hosting internally
- Port 6969 open for the AKI Server
- UDP Port open for P2P traffic, default 25565 (if using UPnP this is not required)
- SPT installed and working, matching the version of MPT you are going to use
- Access to your Windows Firewall
- Internet speed of at least 20 Mbit/s up and down is recommended. Each client averages around 400 kbit/s.

### Client

- Router and ISP that supports either **Port Forwarding** or **UPnP** | **NOTE**: This is only required if you will be hosting in-game
- UDP Port open for P2P traffic, default 25565 (if using UPnP this is not required) | **NOTE**: Same as above
- SPT installed and working, matching the version of MPT you are going to use
- Access to your Windows Firewall
- Internet speed of at least 20 Mbit/s up and down is recommended

### Both

- The latest MPT files

## Hardware Requirements

These are recommendations for a smooth experience:

- **CPU**: i7 8700k / Ryzen 7 2700x
- **GPU**: GTX 1060 / RX 580
- **Memory** 16 GB minimum, 32 GB highly recommended
- **Storage**: SSD is mandatory, do not expect support when running MPT on a HDD

The biggest gain in MPT (and in SPT in general) will be getting a stronger CPU and RAM.

## Installation

### Host using port forwarding

Before starting these steps, make sure you have port forwarded all required ports in the Prerequisites. We will not assist you with opening your ports. If do not have access to your router or can not port forward, use a VPN.

**Firewall Configuration**

1. Port forward the port 6969 TCP in your router (both in and out)
2. Port forward the UDP port that you will use in your router, default 25565 (both in and out)
3. When prompted by Windows, allow connections in your Firewall

**General Setup**

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start up the `Aki.Server.exe` once to let it generate the configuration files for MPT, then close it again
4. Find your WAN IP, you can use [ipv4.icanhazip.com](https://ipv4.icanhazip.com/) as an example
5. Navigate to `user\mods\MPTCoop\config` and open `coopConfig.json`
6. Change `externalIP` to your WAN IP (or VPN IP if using one) found in step 4, then save the file and close it

Example with a fake address (**70.50.130.200**):
```json
{
	"protocol": "http",
	"externalIP": "70.50.130.200"
}
```
7. Find out what your LAN IP is. Open up the `Command Prompt` (Press the start button and search for `cmd` or `command prompt` and press the Enter key)

This is what the command prompt should look like:
![image](https://github.com/mpt-coop/Documentation/assets/20912169/2b089bba-aac2-437e-9a6a-6620a4ba249b)

8. Inside the `Command Prompt`, write the command 'ipconfig' and press the Enter key. Your LAN IP should be the one as demonstrated below:
```bat
Windows IP Configuration


Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : home
   IPv4 Address. . . . . . . . . . . : 192.168.1.120 <------ This is your LAN IP
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
```
9. Go back to the main folder and navigate to `Aki_Data\Server\configs` and open `http.json`
10. Change `ip` to your LAN IP found in step 7, then save the file and close it

Example with a fake LAN address (**192.168.1.120**):
```json
{
	"ip": "192.168.1.120",
	"port": 6969,
	"webSocketPingDelayMs": 90000,
	"logRequests": true,
	"serverImagePathOverride": {	}
} 
```
11. Start the `Aki.Server.exe` and wait for it to finish loading

This is what it should look like when successfully starting:
![image](https://github.com/mpt-coop/Documentation/assets/20912169/fe46fb2d-4e90-4f54-b159-745a1561772a)

12. Start `Aki.Launcher.exe` and click 'Settings'
13. In the `URL` field, change it to reflect your WAN IP. Using the example in step 6 it would be: `http://70.50.130.200:6969` (remember to remove any trailing forward slashes `/`)

### Host using a VPN

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start up the `Aki.Server.exe` once to let it generate the configuration files for MPT, then close it again
4. Navigate to `user\mods\MPTCoop\config` and open `coopConfig.json`
5. Change `externalIP` to your VPN IP, then save the file and close it

Example with a fake address (**20.20.56.73**):
```json
{
	"protocol": "http",
	"externalIP": "20.20.56.73"
}
```
9. Go back to the main folder and navigate to `Aki_Data\Server\configs` and open `http.json`
10. Change `ip` to your VPN IP, then save the file and close it

Example with a fake address (**20.20.56.73**):
```json
{
	"ip": "20.20.56.73",
	"port": 6969,
	"webSocketPingDelayMs": 90000,
	"logRequests": true,
	"serverImagePathOverride": {	}
} 
```
11. Start the `Aki.Server.exe` and wait for it to finish loading
12. Start `Aki.Launcher.exe` and click 'Settings'
13. In the `URL` field, change it to reflect your VPN IP. Using the example in step 5 it would be: `http://20.20.56.73:6969` (remember to remove any trailing forward slashes `/`)

### Client using port forwarding

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start `Aki.Launcher.exe` and click 'Settings'
4. In the `URL` field, change it to reflect the hosts WAN IP. Using the example in "Host using port forwarding" it would be: `http://70.50.130.200:6969` (remember to remove any trailing forward slashes `/`)
5. If hosting in-game, allow all connections (public and private) when prompted by the Windows Firewall

### Client using a VPN

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start `Aki.Launcher.exe` and click 'Settings'
4. In the `URL` field, change it to reflect the hosts VPN IP. Using the example in step 5 it would be: `http://20.20.56.73:6969` (remember to remove any trailing forward slashes `/`)
5. If hosting in-game, allow all connections (public and private) when prompted by the Windows Firewall

## Credits

**Project** | **License and credits**
----------- | -----------------------------------------------------------------------
Aki.Modules | [NCSA](https://dev.sp-tarkov.com/SPT-AKI/Modules/src/branch/master/LICENSE.md) For original patches that are overwritten for MPT compatibility
SIT         | Unlicensed (MPT is based on commit [9de30d8](https://github.com/stayintarkov/StayInTarkov.Client/blob/9de30d8bab1a4cd5e8bb7bcf5d32539098e97aa6/README.md))
Open.NAT    | [MIT](https://github.com/lontivero/Open.NAT/blob/master/LICENSE) For UPnP implementation
LiteNetLib  | [MIT](https://github.com/RevenantX/LiteNetLib/blob/master/LICENSE.txt) For server/client implementation