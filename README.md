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

This was previously 16 frames, but I reduced it to 8 due to the crazy amount of traces needed (and the large amount of time to animate it). I also limited each LED to 2 frames at maximum and reduced the amount of LEDs per firework.
8 frames should be easier to route and less expensive for me to manufacture, lol

The LEDs are also updated to be the correct colors. I decided to make the tails white, so I needed to make the other LEDs able to run at about the same voltage. Blue and some greens and yellows can do 2.9-3.2v (what white typically runs at). I want to have similar/the same voltages so I do not need to spend so much time soldering and setting the correct resistors. 

### Hardware
- While I originally planned to use a 555 timer, the MIP557 is made to be used in astable mode so I will use that
<img width="516" height="277" alt="image" src="https://github.com/user-attachments/assets/8b3b72af-2929-41d8-a32e-ea15fbf6b658" />


- the pulse will go into a binary incrementer. At first I was going to use make it myself with 3 flip flops but I couldn't find the chips I needed at the ECE shop so I will just use a binary incrementer that is available.
- the output of the incrementer is then demuxed 3:8
- the demuxed output then goes to OR gates for sections that are active for multiple frames
<img width="1406" height="683" alt="image" src="https://github.com/user-attachments/assets/28ddbd11-935d-4805-936a-3dac74770bed" />


- and then the rest of the outputs from the mux and the outputs from the OR gates are sent to the MOSFETs
<img width="613" height="605" alt="image" src="https://github.com/user-attachments/assets/50fb694d-7b4b-444e-b20e-be9e88555426" />

- the LEDs are color coded to what section they are a part of.
- from vote of my friends and family, the stems of the fireworks are white while the bursts are different color. the white LEDs for the stems require a higher voltage than amber and red LEDs I originally planned on using (since I love the color of amber LEDs and red is a nice firework color). I really do not want to sort out ~70 0805 resistors when it came time to solder, so I chose green, blue, and yellow so they would all have the same voltage requirements and therefore the same resistors. 
<img width="877" height="733" alt="image" src="https://github.com/user-attachments/assets/28b7a536-8291-4ed8-a22a-e68317bf63bd" />

#### Prototyping
- I used the 3v output from my STM proto board to power it. The battery will output 3.7v but all of the datasheets say the components can use 3.7v so it's fine.
- I was having difficulty with the output (the gif is short, but yes this is the output)
  
![fail1](https://github.com/user-attachments/assets/8b4588be-a69e-401e-8540-8244573b2ad4)

- This was frustrating since the outputs from the incrementor were displaying properly. (from top to bottom- clock, A0, A1, A2)

<img width="1406" height="683" alt="image" src="https://github.com/user-attachments/assets/60bd02f7-76ab-4bed-8883-6b8b1205d2bc" />


- turns out I had the outputs mismatched. I had the input to the mux (A1 and A0) swapped.

![success1](https://github.com/user-attachments/assets/527ce7e2-857b-435a-8461-82884e2a99ac)

- here it is working (going counting in order - 1 is at the top)

- I also needed to check my sizing now that I actually have my cap. I got the initial measurements from a friend who already graduated
  
<img width="444" height="433" alt="image" src="https://github.com/user-attachments/assets/7fd26642-87f2-49ce-9051-5a281964e2c6" />

<img width="475" height="478" alt="image" src="https://github.com/user-attachments/assets/af1f88b1-2cdb-4204-bb6e-dcb3dba89712" />

- Square width: 23.5 cm
- Button diameter: 2.36 cm

    - I will make the overall board a little less than the square width, and the hole for the button a little larger.

- initial kicad measurements from my friend:
  
<img width="444" height="392" alt="image" src="https://github.com/user-attachments/assets/a3925ce0-62ff-453e-9524-143a7e07a284" /> 
<img width="444" height="392" alt="image" src="https://github.com/user-attachments/assets/4da05b26-eeb8-40f8-8049-24536bebfa62" />

- Rectangle: 24cm, button: 26cm
- rectangle needs to shrink, button is fine :)

- final shape:
<img width="617" height="549" alt="image" src="https://github.com/user-attachments/assets/f411613b-05fe-4cc1-8321-a87e486b3ae0" />




#### PCB Images 😀
- I am still working on the silkscreen
<img width="463" height="412" alt="image" src="https://github.com/user-attachments/assets/d485c053-aaf5-4132-94a4-aa6249da4c5c" />

<img width="463" height="412" alt="image" src="https://github.com/user-attachments/assets/b221860e-c547-4e8b-bbb0-0f7107d869a9" />
<img width="463" height="412" alt="image" src="https://github.com/user-attachments/assets/d00cb994-5be2-46ba-aeb2-7729f13977f3" />

- The trace widths for the main branches are 22mils. there are a maximum of ~8 LEDs per branch so I used the digikey trace width calculator and found this width is fine. there are no internal layers so I didnt need to make it any wider.
- yes, that connector hangs off the edge right now - im going to get to that

- power traces are 40 mils.

##### Silkscreen options:
I made all of these images by coloring over photographs but I am not sure where I'd place them onto the board. i guess that is a good problem to have

<img width="788" height="765" alt="image" src="https://github.com/user-attachments/assets/c7b0b8a3-d0ec-4dc7-bde9-726d941adca0" />
