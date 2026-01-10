# Acoustic camera hardware

## Microcontroller
For the Microcontroller a raspberry pi rp2350 was chosen because of the pio interface which could be used to read PDM or i2s microphones. It also has decent comuting power with the dual core cortex m33. With 520kb of RAM, it has more memory than other microcontrollers.To make PCB routing easier a raspberry pi pico 2 will be used.

### Pinout
![](images/pico-2-r4-pinout.svg)

|Data|Lines|gpio|
|-|-|-|
PDM|12|GP0-11|
PDM clock|1||
SPI camera|4|GP12-15|
SPI SD-Card (shared with camera)|1||
SPI Display|4|GP16-19|
Shutter button|1||
|**total**|**23**||






 

## Microphones

### Type
For the microphone there are basically three options:
|  Microphone Type  | Positive               | Negative               | Cost per microphone |
|-------------------|------------------------|------------------------|---------------------|
| Analog | low cost per microphone.          |high noise, ADC needed  | 0.30                |
| I2S    | low noise, data in correct format |High cost per microphone| 1.60                |
| PDM    | low noise                         |digital filtering needed| 1.15                |

The PDM microphone gives a good balance between cost and good quality. Only negative point is that an additionnal digital filtering step is needed. As we aim for low BOM cost and a lot of microphones are needed the PDM microphone is chosen. 


### Count
The RP2350 has 
* 12 pio state machines
* 16 DMA channels

It should be possible to add 24 microphones. Two per pio state machine by using left-right functionnality. one sending data on the positive edge and one on the negative. 

A PIO program can separate the channels in blocks of 32bits. This way they can easily be accessed in a array.

### Pattern
|Pattern|Description|Benefits|Drawbacks|
|------|-----------|--------|--------|
|Grid pattern|Arrange 24 microphones in a 5x5 grid by omitting the central one.|- Better suited for simple beamforming algorithms<br>- Easier calculation of microphone positions<br>- Simpler algorithms| - Generates a lot of redundant information due to multiple microphone pairs having the same distance and angle<br>- Inefficient spatial coverage in certain directions|
|Circle pattern|Place one microphone at the center and 23 around it in a circular arrangement.|- Symmetrical layout simplifies signal processing<br>- Uniform distance from center mic| - All microphones are equidistant, leading to identical side lobes<br>- Poor directional resolution and high sidelobe levels<br>- Redundant spatial information|
|Spiral pattern|Arrange microphones in a spiral pattern starting from the center and expanding outward.|- No redundant information captured<br>- Best sidelobe suppression<br>- Improved directional sensitivity| - More complex algorithmic processing required<br>- Difficult to calculate microphone positions precisely<br>- Slight challenges in beamforming calibration|


## Display
The display should have a serial interface as I2C or SPI so it does not occupy too mouch pins on the microcontroller. 
Spi display st7789

## Optic camera
The camera should allow low resolution capturing to not need too mouch ram, be low cost and deliver the Data over a serial interface.

The [arducam HM01b0](https://www.arducam.com/arducam-hm01b0-qvga-spi-camera-module-for-raspberry-pi-pico-2.html) with a cost of CHF 15.- is a good option.

## Battery
A battery is needed to use the camera without a power chord.

