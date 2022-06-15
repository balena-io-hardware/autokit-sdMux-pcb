# Automation kit SD card multiplexer

The automation kit sd card multiplexer is a board that allows a USB host device multiplex a micro-SD card between the USB host and a male micro-SD connector. This allows the host to write to the SD card, and then toggle the multiplexer so that the card is connected to another device instead.

This has applications for automated flashing of linux devices that run from SD cards, or devices with internal eMMC that is flashed via an SD card.

## Architecture

The design is based around a USB hub with SDIO interface, the Microchip USB2640 [Or alternatively, the pin compatible USB2641 - they are interchangable in this design]. This hub has 2 downstream USB ports and an SDIO interface, and has a driver that allows the upstream USB host to interface with media connected to it. 

A 6 channel 2:1 multiplexer is used to multiplex the SDIO signals of the micro-SD card between the male micro-SD connector built into the PCB, and the USB2640 hub. This multiplexer requires a "GPIO" signal to switch between the 2 states. An FTDI USB to GPIO bridge is used to create this signal from the USB host. The FTDI chip is connected to one of the 2 downstream USB ports of the USB2640 hub. 


![block-diagram](documentation/images/sd-mux-arch.jpg?raw=true)

## Capabilities

- interface to a micro-SD card via USB
- Multiplex a micro-SD card between USB host and DUT

## Interface

### Hardware

- USB A cable

### Software

- TBC - in progress - the device is controlled via HID commands sent over USB. 