# GMX
The GMX ( <b>G</b>imasi <b>M</b>odule e<b>X</b>change ) bus has been developed for the Tuino family to easily bring on the platform different RF modules.
It's a very simple bus that essentially exposes different communication buses. The idea was to standardize the layout of the GPIO pins.<br/>Here the layout:<br/>
<img src="/docs/gmx_bus.png"/><br/>
<br/>

## General I/O Pins
* UART: <b>UART_RX</b> and <b>UART_TX</b>
* I2C: <b>SDA</b> and <b>SCL</b>
* SPI: <b>MISO</b>, <b>MOSI</b>, <b>SCLK</b> and <b>CS</b>
* GPIO: GPIO1, GPIO2, GPIO3, GPIO4, GPIO5, GPIO6

## Power Pins
* 3.3V
* GND
* 5V

The standard power supply for GMX modules is 3.3V  and <b>all signal levels are 3.3V</b>. The 5V is not compulsory and has been inserted only for legacy HW that need the 5V rail, avoiding the necessity of adding a step-up converter on the module.

## Module Control Pin
* gmxRESET
* gmxINT
* gmxCONNECT
* IDENT_1Wire

<b>gmxRESET</b>: Reset signal to the GMX Module ( active LOW )

<b>gmxINT</b>: Interrupt pin to signal to the host processor (active LOW ). Usually used when an RX frame is received by the module.

<b>IDENT_1Wire</b>: One-Wire connection to the onboard EEPROM/PROM - usually a  [DS28EC20](https://www.maximintegrated.com/en/products/digital/memory-products/DS28EC20.html). This is currently optional, it's functionality has not yet been implemented. It will allow the host processor to identify the functionalities of the inserted module.<br/>
<br/>
<b>gmxCONNECT</b>: Presence pin. On the module should be pulled UP to VCC (3.3V), the host processor will identify the presence of a module on the bus via this pin.<br/>

## Programming / Debugging Pins
* SWDIO, SWCLK, SWO/V
<br/>
Standard programming/debugging SWD pins. Not all modules will have these pins connected only those that have a programmable MCU on board.

# Alternate Functions
The standard GMX bus specification has alternate functions for the GPIO pins layout.<br/>
* GPIO1 / ADC1 / DAC1
* GPIO2 / ADC2 / DAC2
* GPIO3 / UART2_RX
* GPIO4 / UART2_TX
* GPIO5 / USB_DM
* GPIO6 / USB_DP


# Master or Slave
GMX Modules are mainly <b>Slave</b> devices connected to a host MCU. But you can also deliver <b>Master</b> devices, ie. having the main MCU on the module and driving thought the GMX bus peripherals. In this scenario the 'basic' pin direction get's reversed:<br/>
* gmxRESET becomes output. Reset to the peripheral board
* SPI CS become output. 
* gmxInt  become input. Interrput from the peripheral

# Physical connector
The GMX bus is based on a standard 2x12 pin 0.05" or 1.27 mm pitch connector.<br>
<img src="/docs/female.png"/><br/>
<br>
Click [here](https://www.digikey.ch/product-detail/en/amphenol-fci/20021321-00024T4LF/609-3774-ND/2209104?keywords=609-3774-ND&cur=EUR&lang=en) for an example of the female connector on Digikey<br/>
And [here](https://www.digikey.ch/product-detail/en/harwin-inc/M50-4911245/952-3150-ND/6556204) an example of the male connector.

# Physical dimensions
The maximum dimensions for a GMX module are 30mmx60mm, like in the picture.

