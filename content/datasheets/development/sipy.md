---
title: "SiPy"
aliases:
    - datasheets/development/sipy.html
    - datasheets/development/sipy.md
    - product-info/development/sipy
    - chapter/datasheets/development/sipy
---

![](/gitbook/assets/assets-lil0igdl11z7jos_jpx-lkn7scqkkkb6tqb3uyo-lkn86n8h-hb1oh1idwb-sipy-2.png)

{{% hint style="info" %}}
 Please Note: We have removed the labels from the pictures in the documentation due to inconsistencies with label orientation.  *The LED must be aligned above the USB socket* when inserting or removing a development board from an expansion board/Pytrack/Pysense/Pyscan.
{{% /hint %}}



**Store**: [Buy Here](https://pycom.io/product/sipy)

**Getting Started:** [Click Here](/gettingstarted/connection/sipy)

## Datasheet



The datasheet of the SiPy is available as a PDF File.

<a href="/gitbook/assets/specsheets/Pycom_002_Specsheets_SiPy_v2.pdf" target="_blank"> SiPy Datasheet </a>

## Pinout

The pinout of the SiPy is available as a PDF File

<a href="/gitbook/assets/sipy-pinout.pdf" target="_blank"> SiPy Pinout </a>

![](/gitbook/assets/sipy-pinout.png)

{{% hint style="info" %}}
Please note that the PIN assignments for UART1 \(TX1/RX1\), SPI \(CLK, MOSI, MISO\) and I2C \(SDA, SCL\) are defaults and can be changed via software.
{{% /hint %}}

## Notes

### WiFi

By default, upon booting up the SiPy will create a WiFi access point with the SSID `sipy-wlan-XXXX`, where `XXXX` is a random 4-digit number, and the password `www.pycom.io`.

### Power

The `Vin` pin on the SiPy can be supplied with a voltage ranging from `3.5v` to `5.5v`. The `3.3v` pin on the other hand is output **only**, and must not be used to feed power into the SiPy, otherwise the on-board regulator will be damaged.

### Deep Sleep

Due to a couple of issues with the SiPy design, the module draws more current than it should while in Deep Sleep. The DC-DC switching regulator always stays in high performance mode, which is used to provide the lowest possible output ripple when the module is in use. In this mode, it draws a quiescent current of 10mA. When the regulator is put into ECO mode the quiescent current drops to 10uA. Unfortunately, the pin used to control this mode is out of the RTC domain. This means that it is not usable during Deep Sleep. This results in the regulator remaining in PWM mode, keeping its quiescent current at 10mA. The flash chip also doesn't enter into power down mode as the CS pin floats during Deep Sleep. This causes the flash chip to consume around 2mA of current. To work around this issue a ["deep sleep shield"](../../boards/deepsleep/) is available that attaches to the module and allows power to be cut off from the device. The device can then be re-enabled either through a timer or via a pin interrupt. With the Deep Sleep Shield, the current consumption during deep sleep is between 7uA and 10uA depending on the wake sources configured.

## Tutorials

Tutorials on the SiPy module can be found in the [examples](/tutorials/introduction) section of this documentation. The following tutorials might be of  interest for those using the SiPy:

* [WiFi connection](/tutorials/all/wlan)
* [Sigfox](/tutorials/sigfox)
* [BLE](/tutorials/all/ble)
