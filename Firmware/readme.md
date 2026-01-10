# Acoustic camera Firmware
The ressources of the chosen microcontroller RP2350 are limited. On the firmware development the RAM usage and processing power must be kept low. 

## Resource consideration
### RAM

| What | Data| KB |
|-|-|-|
|Captured data of PDM microphones | 24x20msx3.077Mbit/s | 184|
|pcm data 16 bit| 24x20ms*48000S/sx2B/S|46|
|FFT data normalized 8 bit| 24x20ms*48000S/sx1B/S|23|
|GCC PHAT|276*||


### Processing power


## Firmware creation steps
* PIO code to read multiple pdm microphones
* Just record audio. PDM to PCM filter implemented
* Display driver
* TDOA algorithm implementation in one axis
* GCC-Phat algorithm implementation im one axis
* create image from correlation outputs of two microphone pairs
* create image out of data of all microphones


