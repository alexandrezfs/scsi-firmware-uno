# SCSI Mass Storage firmware for ATmega16u2

This firmware turns your Arduino UNO into a mass storage device. It does this by flashing microchip firmware `ATmega16u2`.
The firmware does the following:

+ Return appropriate descriptors to let the host load the appropriate FAT/SCSI driver.
+ Simulate a virtual FAT16 filesystem.
+ Can handle SCSI read and write commands but will not persist any data on bootloader area `ATmega328p`, nor in `PROGMEM`. Indeed we clear the buffer when the host try to write something on the endpoint. `memset(buf, 0, sizeof(buf));`

## Build

```
$ git clone https://github.com/abcminiuser/lufa lufa
$ cd lufa/Projects
$ git clone https://github.com/alexandrezfs/scsi-firmware-uno
$ cd scsi-firmware-uno
$ make
```

You need to have `avr-gcc` etc in `PATH`.

## Installing

* Place the `ATmega16u2` in DFU update mode by shorting two pins sticking out closest to the USB plug.
* On macOS or Linux install `dfu-programer` and run `make install`.

## License

MIT