# HTTP_Server_OTA
A simple example which demonstrates OTA update by uploading the new firmware to HTTP server on ESP32 devices

## How to use

### Configure the project
Open the project configuration menu (idf.py menuconfig).

In the `Example Connection Configuration` menu:

- Choose the network interface in the Connect using option based on your board. Currently both Wi-Fi and Ethernet are supported.
- If the Wi-Fi interface is used, provide the Wi-Fi SSID and password of the AP you wish to connect to.
- If using the Ethernet interface, set the PHY model under `Ethernet PHY Device` option, e.g. `IP101`

### Build and Flash

Run `idf.py -p PORT flash monitor` to build and flash the project. This command checks if the partition table contains the `ota_data` partition and restores it to an initial state. This allows the newly loaded app to run from the `factory` partition.

### Upload the new firmware using cURL

Use the following command to upload the new firmware image to the device:
`curl -X POST <device IP>/update --data-binary @<filename>`

## Example Output
```
I (7565) example_common: Connected to example_netif_sta
I (7575) example_common: - IPv4 address: 192.168.20.89,
I (7575) example_common: - IPv6 address: fe80:0000:0000:0000:3e61:05ff:fe4c:3600, type: ESP_IP6_ADDR_IS_LINK_LOCAL
I (7585) example: Starting server on port: '80'
I (7595) example: Registering URI handlers
I (9655) wifi:<ba-add>idx:1 (ifx:0, b4:fb:e4:4d:6e:22), tid:0, ssn:0, winSize:64
I (56075) esp_image: segment 0: paddr=00110020 vaddr=3f400020 size=2490ch (149772) map
I (56135) esp_image: segment 1: paddr=00134934 vaddr=3ffb0000 size=03b8ch ( 15244) 
I (56135) esp_image: segment 2: paddr=001384c8 vaddr=40080000 size=07b50h ( 31568) 
I (56155) esp_image: segment 3: paddr=00140020 vaddr=400d0020 size=8b81ch (571420) map
I (56355) esp_image: segment 4: paddr=001cb844 vaddr=40087b50 size=0e0d4h ( 57556) 
I (56375) esp_image: segment 0: paddr=00110020 vaddr=3f400020 size=2490ch (149772) map
I (56425) esp_image: segment 1: paddr=00134934 vaddr=3ffb0000 size=03b8ch ( 15244) 
I (56435) esp_image: segment 2: paddr=001384c8 vaddr=40080000 size=07b50h ( 31568) 
I (56445) esp_image: segment 3: paddr=00140020 vaddr=400d0020 size=8b81ch (571420) map
I (56645) esp_image: segment 4: paddr=001cb844 vaddr=40087b50 size=0e0d4h ( 57556) 
E (56735) example: Rebooting...
```