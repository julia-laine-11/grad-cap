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
#
## Hardware
- there should be a clock sending out a steady pulse (555 or something similar)
<img width="779" height="580" alt="image" src="https://github.com/user-attachments/assets/2fbc1732-e342-4fa0-aeda-2f9a9681c934" />

- the pulse will go into a frequency divider 2x to create a binary incrementer
<img width="1079" height="416" alt="image" src="https://github.com/user-attachments/assets/da937488-dd74-4dd6-b783-9a98b58497d8" />

- the output of the adder should be demuxed 3:8
<img width="707" height="588" alt="image" src="https://github.com/user-attachments/assets/f8155746-456e-4e14-8a02-bf7a7774601a" />

- the demuxed output should control mosfets to turn on different sections of LEDs
<img width="375" height="214" alt="image" src="https://github.com/user-attachments/assets/62a5dc92-0ca1-42d9-b784-878626d9f826" />


### Pulse gen options:
- LRC circuitin that case should these just be 1:5
- 555 timer
- oscillator of some sort

[idea](https://www.ibiblio.org/kuphaldt/electricCircuits/Digital/DIGI_11.html#xtocid92321):
  <img width="558" height="228" alt="image" src="https://github.com/user-attachments/assets/3c256f88-e757-430c-9ce4-6c2dce072461" />


### Binary inrecmenter options:
- 2 jk flip flops acting as frequency dividers?

[circuit:](https://www.allaboutcircuits.com/textbook/digital/chpt-10/edge-triggered-latches-flip-flops/)
[or component
](https://www.digikey.com/en/products/filter/logic/flip-flops/706?s=N4IgjCBcpgnAHLKoDGUBmBDANgZwKYA0IA9lANogAMIAugL7EC0AbMiGpAC4BOArkVIUQAZhDEATHUYgmSaByi8BxMpEpjiEBsykLOywWsoBWaTLYKAlgBMossFQjEADl3viQXAJ4v89zFw0enogA)




