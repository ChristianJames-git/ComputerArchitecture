Christian James - Entire Project (single group)
RedID - 823672623
Key Used - 11011101

Files:
1) GottchaCounter.cct - counts inputs up to 16 clock pulses and then outputs 1
2) SequenceRecognizer.cct - Accepts inputs to either X1 or X0 for a 1 or a 0 input respectively.
                            Uses inputs to generate clock. Implements FSM with the clock triggered
                            upon release of inputs. Uses the GottchaCounter to lock after 16 inputs.
                            Outputs 1 when the correct input sequence, 11011101, is detected.
3) CJames.clf - Library of parts

For the Counter, I used a ripple counter as only counting to 16 wouldn't cause enough delay to
outweight the gate cost benefits.
To obtain my main circuit, I first made a state diagram, then state table, then k-maps and equations.
From there, I implements the equations in circuit form using d flip flops. I didn't use the one-hot
method to save on flip flops. For my inputs, I ORed them then inverted to generate a clock pulse
on the falling edge. To generate X, I ORed the inputs again, but this time I inverted X0 to make X
be 1 or 0 respective to X1 or X0. Finally, to lock the device after 16 inputs, I ORed the lock output
with the clock before its inverter. This locks the clock to 0 when the lock is 1, disallowing future updates
to the flip flops and therefore Z.

