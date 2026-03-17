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


### Hardware
- While I originally planned to use a 555 timer, the MIP557 is made to be used in astable mode so I will use that
- It will have a potentiometer instead of a static resistor so that the frame rate can be sped up/lowered

<img width="331" height="267" alt="image" src="https://github.com/user-attachments/assets/fd8a8c11-7a70-4c9d-b69b-4a8301ea13ad" />

- I did add a footprint for a 555 on the back in case I cannot get this chip to work. I do not have one in person to prototype with.

<img width="176" height="130" alt="image" src="https://github.com/user-attachments/assets/d8366f4b-e523-4377-a559-3d9bf51551d7" />


- the pulse will go into a binary incrementer. At first I was going to use make it myself with 3 flip flops but I couldn't find the chips I needed at the ECE shop so I will just use a binary incrementer that is available.

<img width="696" height="322" alt="image" src="https://github.com/user-attachments/assets/45ac109b-0360-48ba-b455-fc5aa2996721" />

- the output of the incrementer is then demuxed 3:8

<img width="734" height="322" alt="image" src="https://github.com/user-attachments/assets/cdee372b-6701-4d31-8cc1-a08969a0df91" />


- the demuxed output then goes to OR gates for sections that are active for multiple frames

<img width="1406" height="683" alt="image" src="https://github.com/user-attachments/assets/28ddbd11-935d-4805-936a-3dac74770bed" />


- and then the rest of the outputs from the mux and the outputs from the OR gates are sent to the MOSFETs
<img width="613" height="605" alt="image" src="https://github.com/user-attachments/assets/50fb694d-7b4b-444e-b20e-be9e88555426" />

- the LEDs are color coded to what section they are a part of.
- from vote of my friends and family, the stems of the fireworks are white while the blooms are different color.
  
<img width="728" height="611" alt="image" src="https://github.com/user-attachments/assets/6262a701-8356-449d-b8cd-6371e6d786b6" />

LED resistors:
- input: 3.7v  

  - white: 3.1v  20mA
  
    - 3.7-3.1 = .6/.02 = 30

  - amber: 2v 20mA
  
    - 3.7-2 = 1.7/.02 = 85

  - red: 2v 20mA
  
    - 3.7-2 = 1.7/.02 = 85

  - green: 2.2v 20mA
  
    - 3.7-2.2 = 1.5/.02 = 75
   
30 ohms: 16

80 ohms: 51


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
