# Settling Behavior and Error

Consider a finite open-loop gain op-amp with a gain of $A_0$.

![alt text](images/20253003_082400_Finite_Gain_Op_Amp.svg)

Connect this in negative feedback.

![alt text](images/20253003_091200_UG_Feedback.svg)

The closed loop gain is given by $\frac{A_0}{1+A_0}$.

The error voltage is given by $V_{E} = V_{OUT}/A_0 = \frac{1}{1+A_0}$.

Let us take a real schematic and slow down time domain response.

## Settling - Real Circuit

Consider the below circuit.

<p style="text-align:center;"><img src=images/20253003_093000_Real_Circuit.svg width=300>

There are some pretty cool settling to learn from here. Let us start with the operation principle of this circuit.

* Input pair transistors (MN1 and MN2) form a differential pair.  
    * Say $V_{INP}$ > $V_{INN}$. MN1 will have higher $V_{GS}$ and hence higher $I_D$. Less current is sunk in the right branch.
    * Currents are equal when $V_{INP}$ = $V_{INN}$.
    * MP4 copies the current from MP3. At $V_{OUTP}$, higher current is pumped in by MP4 than taken out by MN2. The difference is sent to the load. This causes $V_{OUTP}$ node to rise.

Let us say we connected the above op-amp in unity gain feedback as shown below and an input of 400mV is connected to $V_{INP}$.

<p style="text-align:center;"><img src=images/20253003_171700_Real_Circuit_Unity_Gain.svg width=300>

Due to the finite gain of the op-amp, output did not settle to 400mV. Instead, it settled to 407mV. We will see the exact mechanism of this error later.

Now, let us increase the input abruptly to 1.4V and look at:
* Input voltage
* Output voltage
* Internal gate voltage (PMOS gate) = PGATE

Initially, nothing will happen. The op-amp will be too sluggish to respond much. Almost all of the bias current will be in the left branch and this will be copied to the right side.

