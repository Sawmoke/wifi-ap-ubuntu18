# Create Access Point Wifi Ubuntu Server 18.04 LTS

This is a brief tutorial on how to get working wifi hotspot via command line in Ubuntu Server 18.04 LTS

## Requirements

Install wifi-ap via snap packet manager

```bash
sudo snap install wifi-ap
```

## Usage
After installation it will try to start a wifi ap with default config parameters.
If this is not the case you may want to set the right parameters according to your conditions.
You can follow [this](https://docs.ubuntu.com/core/en/stacks/network/wifi-ap/docs/reference/configuration) reference for configuration commands.
In my case the only wrong default configuration was about the interface name. To get your own wifi interface name you can run

```bash
networkctl | awk '/wlan/ {print $2}'
```

Then you just need to edit default configuration by
```bash
sudo wifi-ap.config set wifi.interface=wlx0c9d92b943c4
```
And then enable wifi access point

```bash
sudo wifi-ap.config set disabled=False
```
You can also edit your SSID name and WPA password with
```bash
sudo wifi-ap.config set wifi.ssid=MyTestSSID
sudo wifi-ap.config set wifi.security=wpa2
sudo wifi-ap.config set wifi.security-passphrase=Test1234
```


## Reference
[Wifi-ap](https://docs.ubuntu.com/core/en/stacks/network/wifi-ap/docs)
## License
[MIT](https://choosealicense.com/licenses/mit/)
