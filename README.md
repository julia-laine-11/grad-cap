# grad-cap
This is a pcb for my grad cap

## Physical:
- the pcb should cover the whole cap
- the pcb should have a space for the little tassle knob in the middle
- the battery should be flat and fit underneath the cap or pcb
- the fireworks should move while the power is on

- For appearances, I want to make the entire circuit from gates since i think more chips is cute

solely LED layout:
  <img width="842" height="854" alt="image" src="https://github.com/user-attachments/assets/155d88c5-154f-440f-a806-3de5e786ce96" />

the lines will not be visible. those are on layers user1, 2 and 3

## Hardware
- there should be a clock sending out a steady pulse
- the pulse should increment a binary incrementer/adder
- the output of the adder should be demuxed
- the demuxed output should control mosfets to turn on different sections of LEDs

### Pulse gen options:
- LRC circuit
- 555 timer
- oscillator

[idea](https://www.ibiblio.org/kuphaldt/electricCircuits/Digital/DIGI_11.html#xtocid92321):
  <img width="558" height="228" alt="image" src="https://github.com/user-attachments/assets/3c256f88-e757-430c-9ce4-6c2dce072461" />



### Binary inrecmenter options:
- positive or negative triggered flip flops in series
- each feeds into the previous
- the final one feeds from the clock
- basically cuts the frequency in half every time :)
- i should not have to worry about prop delays since this circuit should be visible to the eye and not as fast as possible 

[circuit:](https://www.allaboutcircuits.com/textbook/digital/chpt-10/edge-triggered-latches-flip-flops/)
[or component
](https://www.digikey.com/en/products/filter/logic/flip-flops/706?s=N4IgjCBcpgnAHLKoDGUBmBDANgZwKYA0IA9lANogAMIAugL7EC0AbMiGpAC4BOArkVIUQAZhDEATHUYgmSaByi8BxMpEpjiEBsykLOywWsoBWaTLYKAlgBMossFQjEADl3viQXAJ4v89zFw0enogA)
