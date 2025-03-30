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

Let us say we connected the above op-amp in unity gain feedback as shown below and an input of 1.8V is connected to $V_{INP}$. See a spice simulation result below.

<img src=images/20253003_220600_Simulation_Unity_Gain.png width=500>

Due to the finite gain of the op-amp, output did not settle to 1.8V. Instead, it settled to 1.804V. We will see the exact mechanism of this error later. Let us make some note of the behaviour of this error at this moment.

* Error = 1.804/1.8 = 0.22%.
* Increase the input to 2.8V. Error = 2.795/2.8 = -0.17%
* Set the input to 2.3V. Error = 2.3/2.3 $\approx$ 0%. What is special about 2.3V? This is the PMOS diode voltage. We will talk about all of this later.

Now, let us increase the input abruptly to 2.8V from 1.8V and look at:
* Input voltage
* Output voltage
* Internal gate voltage (PMOS gate) = PGATE

See a zoomed out view below.

![alt text](images/20253003_223300_Simulation_Unity_Gain.png)

In the zoomed out view, initially output is slightly higher than input and finally output is slightly lower than input. The values are same as the DC values.

See a zoomed in view below.

![alt text](images/20253003_223700_Simulation_Unity_Gain.png)

Initially, nothing will happen. The op-amp will be too sluggish to respond much. Almost all of the bias current will be in the left branch and this will be copied to the right side. For about 120mV input voltage movement, output voltage moves by 62mV. See this below.

![alt text](images/20253003_224400_Voltage_Movement.png)

Output will steadily increase. Eventually it will overshoot the input level at which point MN2 start taking more current. This will then settle back.

Notice how PGATE settles below.

![alt text](images/20253003_225000_PGATE.png)

PGATE never settles to the initial value. We will discuss this later.

