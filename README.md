# airco2ntrol

airco2ntrol is a simple tool to read/print values from a [TFA Dostmann 'AirCO2ntrol Mini'](https://www.tfa-dostmann.de/en/produkt/co2-monitor-airco2ntrol-mini/) CO2 monitor.

## Hardware

Pictures of the tear down on a [Russian page](https://habr.com/en/company/masterkit/blog/248403/) and its [Googlish English](https://translate.google.com/translate?hl=&sl=ru&tl=en&u=https%3A%2F%2Fhabr.com%2Fen%2Fcompany%2Fmasterkit%2Fblog%2F248403%2F) translation.

## Official Documentation

The [user manual](http://co2meters.com/Documentation/Manuals/Manual-RAD-0301.pdf) and the [USB Communication Protocol](http://www.co2meters.com/Documentation/AppNotes/AN135-CO2mini-usb-protocol.pdf).

## Configuration

Use `dmesg` to find the device path. Look for vendor `04d9` and product `a052`:

```
[    2.259541] usb 1-5.2: New USB device found, idVendor=04d9, idProduct=a052, bcdDevice= 1.00
[    2.259663] usb 1-5.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.259778] usb 1-5.2: Product: USB-zyTemp
[    2.259865] usb 1-5.2: Manufacturer: Holtek
[    2.259953] usb 1-5.2: SerialNumber: 1.40
[    2.270086] hid-generic 0003:04D9:A052.0006: hiddev2,hidraw5: USB HID v1.10 Device [Holtek USB-zyTemp] on usb-0000:00:14.0-5.2/input0
```

The first parameter of `open()` should be set to `"/dev/hidraw5"` (airco2ntrol.py).
