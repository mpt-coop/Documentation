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

- You may only share MPT as long as proper credits are given, it is not used for commercial purposes and you do not modify it.
- You may not monetize your server in terms of payments or donations.
- You may not host massive public servers, MPT is meant for COOP with your friends.
- You may not copy and/or replicate the code by MPT, nor may you use its assets that are handcrafted by our developers and artists.

## Prerequisites

MPT requires general knowledge of computers, networking and Aki. If you are not comfortable with these concepts, this project is not for you. Please try to understand and respect this.

### Hosting

- Router and ISP that supports either **Port Forwarding** or **UPnP**
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

1. Port forward the port 6969 **TCP** in your router (both in and out)
2. Port forward the **UDP** port that you will use in your router, default 25565 (both in and out)
3. When prompted by Windows, allow ***all*** connections in your Firewall

**General Setup**

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start up the `Aki.Server.exe` once to let it generate the configuration files for MPT, then close it again
4. Go back to the main folder and navigate to `Aki_Data\Server\configs` and open `http.json`
5. Change `ip` to `0.0.0.0`, then save the file and close it
6. Navigate to `user\mods\mpt-server\assets\configs` and open `mpt.jsonc`
7. Change any of the settings according to your likings.
    - **useBtr**: if the BTR should spawn or not when playing Streets
	- **friendlyFire**: if friendly fire should be enabled or not
	- **dynamicVExfils**: automatically scale vehicle exfils max players with the amount of players in the raid
	- **allowFreeCam**: allow players to freely toggle free cam during raids
    - **giftedItemsLoseFIR**: if sent items should lose their FiR status
8. Start the `Aki.Server.exe` and wait for it to finish loading
    - This is what it should look like if it succeeded to start:
    ```
    Started webserver at http://0.0.0.0:6969
    Started websocket at ws://0.0.0.0:6969
    Server is running, do not close while playing SPT, Happy playing!!
    ```
9. Start `Aki.Launcher.exe`
10. Your friends can connect to your server using your WAN IP, which can be found using the [IPv4.ICanHazIP](https://ipv4.icanhazip.com/) site

### Host using a VPN

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start up the `Aki.Server.exe` once to let it generate the configuration files for MPT, then close it again
4. Go back to the main folder and navigate to `Aki_Data\Server\configs` and open `http.json`
5. Change `ip` to your VPN IP, then save the file and close it

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
6. Navigate to `user\mods\mpt-server\assets\configs` and open `mpt.jsonc`
7. Change any of the settings according to your likings.
    - **useBtr**: if the BTR should spawn or not when playing Streets
	- **friendlyFire**: if friendly fire should be enabled or not
	- **dynamicVExfils**: automatically scale vehicle exfils max players with the amount of players in the raid
	- **allowFreeCam**: allow players to freely toggle free cam during raids
    - **giftedItemsLoseFIR**: if sent items should lose their FiR status
8. Start the `Aki.Server.exe` and wait for it to finish loading
    - This is what it should look like if it succeeded to start using the example IP in step 5:
    ```
    Started webserver at http://20.20.56.73:6969
    Started websocket at ws://20.20.56.73:6969
    Server is running, do not close while playing SPT, Happy playing!!
    ```
9. Start `Aki.Launcher.exe` and click 'Settings'
10. In the `URL` field, change it to reflect your VPN IP. Using the example in step 5 it would be: `http://20.20.56.73:6969` (remember to remove any trailing forward slashes `/`)

### Client using port forwarding

1. Download the latest MPT build
2. Navigate to your SPT installation and extract the contents of the archive into the folder
3. Start `Aki.Launcher.exe` and click 'Settings'
4. In the `URL` field, change it to reflect the hosts WAN IP (remember to remove any trailing forward slashes `/`)
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
Aki.Modules | [NCSA](https://dev.sp-tarkov.com/SPT-AKI/Modules/src/branch/master/LICENSE.md) (For original patches that are overwritten for MPT compatibility)
SIT         | Unlicensed (MPT is based on commit [9de30d8](https://github.com/stayintarkov/StayInTarkov.Client/blob/9de30d8bab1a4cd5e8bb7bcf5d32539098e97aa6/README.md))
Open.NAT    | [MIT](https://github.com/lontivero/Open.NAT/blob/master/LICENSE) (For UPnP implementation)
LiteNetLib  | [MIT](https://github.com/RevenantX/LiteNetLib/blob/master/LICENSE.txt) (For server/client implementation)
