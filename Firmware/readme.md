# Acoustic camera Firmware
The ressources of the chosen microcontroller RP2350 are limited. On the firmware development the RAM usage and processing power must be kept low. 

## Resource consideration
### RAM
Avaliable RAM: 520KB


| What | Data| KB |
|-|-|-|
|Captured data of PDM microphones | 24 x 20msx3.077Mbit/s | 184|
|pcm data 16 bit| 24x20ms x 48000S/s x 2B/S|46|
|FFT data normalized 8 bit| 24 x 20ms x 48000S/s x 1B/S|23|
|GCC PHAT|2 x 20ms x 4800S/s x 1B/S + 24 x 23 x 0.5 x  4 x 0.5ms x 48000S/s x 1 B/S x 2|14|
|Image|2x84x84x1Byte|14|
|**Total**||**281**|





### Processing power


## Firmware creation steps
* PIO code to read multiple pdm microphones
* Just record audio. PDM to PCM filter implemented
* Display driver
* TDOA algorithm implementation in one axis
* GCC-Phat algorithm implementation im one axis
* create image from correlation outputs of two microphone pairs
* create image out of data of all microphones


