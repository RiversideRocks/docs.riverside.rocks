# qBittorrent

qBittorrent is an [open-source](https://github.com/qbittorrent/qBittorrent) torrent client. Not only can the client be installed on Windows, Mac, and Linux, but it is possible to run it on the web with a slick (but slightly outdated) interface.

![](https://i.imgur.com/PPIM6Xr.png)

## Getting Started

Using qBittorrent is quite simple. Begin by downloading it from [their website](https://www.qbittorrent.org/download.php) and running the installer. Upon installing, you should see an image similar to the one displayed above. To add a torrent file or magnet link, click on the "link" button in the top left corner.

![](https://i.imgur.com/4PkTT6I.png)

You should then see a large textbox apear. Paste your torrent/magnet link into this box, then click "Download". Congratulations, you've began downloading a torrent in qBittorrent!

## Binding to a VPN

When using a VPN, you should never trust the VPN client killswitch feature. Instead, you should bind your client to the VPN's network interface. This is an effective solution for preventing traffic leaks. First, go to hover over the "Tools" tab, then click on "Preferences" (alternatively, you can run ALT+O on Windows and Linux). Then, click on "Advanced". You should see a box where you can set your network interface to bind to. To determine what this interface is, see [Network Interfaces](/VPN/network-interface). If your VPN isn't on this list, the interface likley contains the name of your VPN in it.

## qBittorrent web

qBittorrent has a web interface that allows you to torrent from any device. A great application for this is to buy a VPS that allows torrenting control qBittorent on the VPS from a laptop.

### CLI Setup (Ubuntu/Debian)

To set up the web interface from the command line on Ubuntu and Debian, first make sure the correct software is installed. Update your packages and check if `qbittorrent-nox` is installed.

```
sudo apt-get update
sudo apt-get install qbittorrent-nox
```

Once `qbittorrent-nox` is installed, start the client.

```
qbittorrent-nox --webui-port=8080
```

The `webui-port` argument allows you to change the port of the web client. The client will run at your machine's IP (`localhost` if on a laptop). The default username and password are `admin` and `adminadmin`, respectively.

### GUI Setup

To set up the web interface from the GUI, click on Tools --> Preferences --> WebUI. Check off the "Web User Interface (Remote Control)" checkbox, and edit the settings that follow. The client will run at your machine's IP (`localhost` if on a laptop). The default username and password are `admin` and `adminadmin`, respectively.

## Security

The client runs on 0.0.0.0, meaning that it binds to every available IP address of your machine, so you may need to update your firewall settings. You can force the client the bind to a specific IP address in the GUI settings.n**Make sure to change the default password for the interface**, and consider running it on a port other than 8080.

> Last Updated: 10/15/2022