# Acoustic camera hardware
## Component selection
### Microcontroller
For the Microcontroller a raspberry pi rp2350 was chosen because of the pio interface which could be used to read PDM or i2s microphones. It also has decent comuting power with the dual core cortex m33. With 520kb of RAM, it has more memory than other microcontrollers.

### Microphone
For the microphone there are basically three options:
|  Microphone Type  | Positive               | Negative               | Cost per microphone |
|-------------------|------------------------|------------------------|---------------------|
| Analog | low cost per microphone.          |high noise, ADC needed  | 0.30                |
| I2S    | low noise, data in correct format |High cost per microphone| 1.60                |
| PDM    | low noise                         |digital filtering needed| 1.15                |

The PDM microphone gives a good balance between cost and good quality. Only negative point is that an additionnal digital filtering step is needed. As we aim for low BOM cost and a lot of microphones are needed the PDM microphone is chosen. 


### Display
The display should have a serial interface as I2C or SPI so it does not occupy too mouch pins on the microcontroller. 
Spi display st7789

### Optic camera
The camera should allow low resolution capturing to not need too mouch ram, be low cost and deliver the Data over a serial interface.

The [arducam HM01b0](https://www.arducam.com/arducam-hm01b0-qvga-spi-camera-module-for-raspberry-pi-pico-2.html) with a cost of CHF 15.- is a good option.


### Battery
A battery is needed to use the camera without a power chord. 

## ?

### How many microphones?
The RP2350 has 
* 12 pio cstate machines
* 16 DMA channels

### microphone arrangement
