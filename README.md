# Hoymiles Zero Export Control / Hoymiles Nulleinspeisung

## Introduction
Hoymiles Zero Export is a Python script for managing the power of the Hoymiles inverters to reduce the amount of the generated power to the grid. Based on the current power output, the script can automatically adjust the export limit of the inverter, allowing for optimal energy management.

## Prerequisites
Before running this script make sure you have a powermeter which outputs a negative power value in case of returning to the grid.
For example: the Holley DTZ541 shows -150W if the solar inverter is overproducing.
This script does not use MQTT, it's based on webapi communication.

### Supported Smart-Meter Modules:
- [Tasmota Smart Meter Interface](https://tasmota.github.io/docs/Smart-Meter-Interface/) (e.g. "[Hichi IR Lesekopf](https://www.ebay.de/sch/i.html?_ssn=hicbelm-8)" or equal)
- [Shelly EM, Shelly 3EM, Shelly 3EM Pro, Shelly 1PM, Shelly Plus 1PM](https://www.shelly.cloud/de/products/product-overview/shelly-3em-1)
- [SHRDZM Smartmeter Modul](https://cms.shrdzm.com/produkt/smartmeter-modul/)
- [Emlog ("electronic meter log")](https://weidmann-elektronik.de/Emlog_Projekt.html)
- [VZLogger](https://wiki.volkszaehler.org/software/controller/vzlogger) with [local http api](https://wiki.volkszaehler.org/software/controller/vzlogger/vzlogger_conf_parameter#local)
- [ioBroker](https://www.iobroker.net/) with [simpleAPI](https://github.com/ioBroker/ioBroker.simple-api)
- [HomeAssistant](https://www.home-assistant.io/)
- easy to implement new smart meter modules supporting WebAPI / JSON

### Supported DTU and Inverters
- [Ahoy](https://github.com/lumapu/ahoy) - this script is developed with AHOY and therefore i recommend it
- [OpenDTU](https://github.com/tbnobody/OpenDTU)
- Hoymiles HM-Series Inverter (since V1.7 multiple inverters are supported) like [1-in-1](https://www.hoymiles.com/product/microinverter/hm-300-350-400-eu/), [2-in-1](https://www.hoymiles.com/product/microinverter/hm-600-700-800-eu/) or [4-in-1](https://www.hoymiles.com/product/microinverter/hm-1200-1500-eu/)

### Support of battery powered Hoymiles Inverters
With Version 1.28 and higher you can set various limits to support battery powered Hoymiles Inverters
- power-off limit
- limit reduction if battery voltage drops
- auto-power-on if battery voltage rises 

## Examples in Home-Assistant:
![qkeo2J4U](https://user-images.githubusercontent.com/111107925/222456008-947bfbf1-09b3-4639-97d0-cc88c5af2a72.png)
![IMG_E0136](https://user-images.githubusercontent.com/111107925/217559535-1b530738-67bc-4c29-a6f2-9aa4addce41d.JPG)

## Linux installation

Make sure you have Python 3.9.2 or greater installed:
```sh
python3 --version
```
if you don´t have python installed or an older version is on your machine, then [install or upgrade](https://docs.python.org/3.11/using/unix.html#on-linux) it

Get the code and unpack the archive:
```sh
wget https://github.com/reserve85/HoymilesZeroExport/archive/refs/heads/main.zip
unzip main.zip
rm main.zip
mv HoymilesZeroExport-main/ HoymilesZeroExport/
cd HoymilesZeroExport/
```

Launch installscript to create zero export service
```sh
sudo chmod +x install.sh
sudo ./install.sh
```

Edit your configuration, save with ctrl + s, exit with ctrl + x
```sh
sudo nano HoymilesZeroExport_Config.ini
```

Restart the service after modified configuration or script
```sh
sudo ./restart.sh
```

View the output log
```sh
sudo journalctl -u HoymilesZeroExport.service -n 20000 -e -f
```

If you really don´t want the service anymore, just uninstall it
```sh
sudo ./uninstall_service.sh
```

## Windows installation
Get Python 3 (download is available at https://www.python.org/) and then install the module "requests":
```sh
pip3 install requests
```
Now you can execute the script with python.

## Special thanks to:
- https://github.com/lumapu/ahoy
- https://github.com/tbnobody/OpenDTU
- https://tasmota.github.io/docs/Smart-Meter-Interface/
- https://ottelo.jimdofree.com/stromz%C3%A4hler-auslesen-tasmota/
- https://hessburg.de/tasmota-wifi-smartmeter-konfigurieren/

## Donate
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://paypal.me/TobiasWKraft/5)

Please support me if you like this project by spending me a coffee instead of giving away your electricity.
