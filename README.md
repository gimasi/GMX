# GMX
The GMX bus has been developed for the Tuino platform to easily bring on the platform different RF modules. <br/>
Its a very simple bus that essentially exposes different communication buses. The idea was to standardize the layout of the possible communication buses and generic GPIO pins. Here the layout:<br/>
<img src="/docs/gmx_bus.png"/><br/>
<br/>

## General I/O Pins
* UART: <b>UART_RX</b> and <b>UART_TX</b>
* I2C: <b>SDA</b> and <b>SCL</b>
* SPI: <b>MISO</b>, <b>MOSI</b>, <b>MOSI</b>, <b>SCLK</b> and <b>CS</b>
* GPIO: GPIO1, GPIO2, GPIO3, GPIO4, GPIO5, GPIO6

## Module Control Pin
* gmxRESET
* gmxINT
* gmxCONNECT
* IDENT_1Wire

<b>gmxRESET<b/>: Reset signal to the GMX Module ( active LOW )

<b>gmxINT<b/>: Interrupt pin to signal to the host processor (active LOW ). Usually used when an RX frame is received by the module.

<b>IDENT_1Wire</b>: One-Wire connection to the onboard EEPROM/PROM - usually a  [DS28EC20](https://www.maximintegrated.com/en/products/digital/memory-products/DS28EC20.html). This is currently optional, it's functionality will be described in the upcoming months, when the host processor will be able to identify the functionalities of the module by reading the EEPROM.<br/>
<br/>
<b>gmxCONNECT</b>: Presence pin. On the module should be pulled UP a VCC (3.3V), the host processor will identify the presence of a module via this pin.<br/>


## Programming / Debugging Pins
* SWDIO, SWCLK, SWO/V


