# grad-cap
This is a pcb for my grad cap

## Physical:
- the pcb should cover the whole cap
- the pcb should have a space for the little tassle knob in the middle
- the battery should be flat and fit underneath the cap or pcb
- the fireworks should move while the power is on
#
### LED Sequence:

![WhatsApp Video 2026-01-28 at 01 59 47](https://github.com/user-attachments/assets/233ab3e7-62e2-4c4f-bd1b-c888495b62f6)

This was previously 16 frames, but I reduced it to 8 due to the crazy amount of traces needed. I also limited each LED to 2 frames at maximum and reduced the amount of LEDs per firework.
8 frames should be easier to route and less expensive for me to manufacture, lol

The LEDs are also updated to be the correct colors. I decided to make the tails white, so I needed to make the other LEDs able to run at about the same voltage. Blue and some greens and yellows can do 2.9-3.2v (what white typically runs at). I want to have similar/the same voltages so I do not need to spend so much time soldering and setting the correct resistors. 

### Hardware
- While I originally planned to use a 555 timer, the MIP557 is made to be used in astable mode so I will use that
<img width="516" height="277" alt="image" src="https://github.com/user-attachments/assets/8b3b72af-2929-41d8-a32e-ea15fbf6b658" />


- the pulse will go into a frequency divider 3x to create a binary incrementer. At first I was going to use the 555/557 output as the LSB, but for timings sake it will be more reliable to use the flip flops for the LSB
<img width="935" height="639" alt="image" src="https://github.com/user-attachments/assets/de3db092-284d-4b73-95cd-af5b752a20c3" />


- the output of the adder is then demuxed 3:8
<img width="447" height="401" alt="image" src="https://github.com/user-attachments/assets/57ecdfec-9c2c-443d-a55f-b9b3ee59cd2b" />

- the demuxed output then goes to OR gates for sections that are active for multiple frames
<img width="752" height="592" alt="image" src="https://github.com/user-attachments/assets/b3137ebb-3cf7-4186-88eb-9d0848af02d3" />

- and then the rest of the outputs from the mux and the outputs from the OR gates are sent to the MOSFETs
<img width="613" height="605" alt="image" src="https://github.com/user-attachments/assets/50fb694d-7b4b-444e-b20e-be9e88555426" />

- the LEDs are color coded to what section they are a part of.
- from vote of my friends and family, the stems of the fireworks are white while the bursts are different color. the white LEDs for the stems require a higher voltage than amber and red LEDs I originally planned on using (since I love the color of amber LEDs and red is a nice firework color). I really do not want to sort out ~70 0805 resistors when it came time to solder, so I chose green, blue, and yellow so they would all have the same voltage requirements and therefore the same resistors. 
<img width="877" height="733" alt="image" src="https://github.com/user-attachments/assets/28b7a536-8291-4ed8-a22a-e68317bf63bd" />

#### PCB Images 😀
- I am still working on the silkscreen
<img width="994" height="898" alt="image" src="https://github.com/user-attachments/assets/6c532f59-1e33-4202-ba3b-e867afa7218b" />

<img width="788" height="765" alt="image" src="https://github.com/user-attachments/assets/7cbcc828-5071-465b-b571-d3de6f5eaad6" />

<img width="788" height="765" alt="image" src="https://github.com/user-attachments/assets/f74eb3aa-8ada-4aad-9a3f-a9adcfbe3377" />

- The trace widths for the main branches are 22mils. there are a maximum of ~8 LEDs per branch so I used the digikey trace width calculator and found this width is fine. there are no internal layers so I didnt need to make it any wider.

- power traces are 40 mils.

##### Silkscreen options:
I made all of these images by coloring over photographs but I am not sure where I'd place them onto the board. i guess that is a good problem to have

<img width="788" height="765" alt="image" src="https://github.com/user-attachments/assets/c7b0b8a3-d0ec-4dc7-bde9-726d941adca0" />
