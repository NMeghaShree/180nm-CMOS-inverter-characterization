# CMOS-inverter-characterization
This project involves designing of a CMOS inverter in order to do its transient analysis, calculate propagation delay, rise and fall times, etc. The schematic is made in LTSpice and model file is created with following properties:-  

*I)NMOS:-*
Vton=1V; Wn=8um; Ln=2um; kn'=50 uA/ V sq.; gamma=0; Lambda=0;  
*II)PMOS:-*
Vtop=-1V; Wp=8um; Lp=2um; kp'=50 uA/ V sq.; gamma=0; Lambda=0; 

The load capacitance is taken as, Cload= 1pf.
Other constraints:-
for input wave, delay time=8ns; rise time=5ns; fall time=5ns; on time= 20ns; time period=60ns
this implies, duty cycle ratio=1/3

Using these, we design the following schematic and do the transient analysis for a duration of 50ns with Vin=5V, Vdd=Vs=5V.
![schem](https://github.com/user-attachments/assets/906ec6b4-6957-454f-a29a-79cb9fe30b29)

The following input and output waveforms  will be obtained:-  
<img src="https://github.com/user-attachments/assets/8f0ddcc1-9e08-4f6e-8aa8-8dc55baeb8a9" alt="vin" width="400" height="200">
<img src="https://github.com/user-attachments/assets/7745d26f-b339-4be8-b732-59c8c1bab520" alt="vout" width="400" height="200">  

Now, our aim is to calculate the rise and fall times and propagation delay theoretically and verify it against the values obtained from the logfile of LTSpice.  

Result obtained from log file:-  
<img src="https://github.com/user-attachments/assets/ee733816-c1c7-4201-a744-1ecf26b49f54" alt="log" width="400" >    
The Propagation delay(low to high, tpLH) is the time delay between the 50% transition of input voltage(when it goes from high to low) and 50% transition of output voltage (when it goes from low to high).  
The Propagation delay(high to low, tpHL) is the time delay between the 50% transition of input voltage(when it goes from low to high) and 50% transition of output voltage (when it goes from high to low).    
<img src="https://github.com/user-attachments/assets/03e41912-acdb-40ed-b3f8-cd12726f8d91" alt="cmos delay" width="400" height="200">  

The total propagation delay is the average of tpLH and tpHL. As we have designed a symmetric CMOS inverter, the propagation delays for the transition are approximately same:-  
tpHL= 2.80449 ns  
tpLH= 2.80447 ns  
Total propagation delay= 2.80448 ns  

Now, we will try to get the rise and fall times. Rise time is defined as the time needed for the output to go from 10% to 90% of its value. Fall time is defined as the time required for the output to go from 90% to 10% of its value. From the logfile, we can see that:-  
Rise time=4.15745 ns  
Fall time=4.15579 ns  

Now, we will try to estimate the power dissipation in the CMOS inverter. The one cycle, the I(leakage) at output and power dissipation curve look like the following:-  
First one is the I(leakge) curve, second one is the power dissipation curve.   
Power Dissipation=Vdd* I(leakage)  watts  
Vdd=5V(constant)  

<img src="https://github.com/user-attachments/assets/8640c8dd-abc7-4f3b-ab97-057e2b4b57e2" alt="i leak" width="400" height="200">  
<img src="https://github.com/user-attachments/assets/27bc4a99-7abe-4d20-ab01-1c9abfdf7389" alt="power" width="400" height="200">   

Power dissipation here is around 7.7 milli-watts.  

The power dissipation curve for numerous cycles look like:-  
<img src="https://github.com/user-attachments/assets/d3cfcb94-e930-48aa-ae9a-78ca67260b16" alt="ideal power curve" height="400" width="700" >  
 The average power for both the transitions is :-    
  <img src="https://github.com/user-attachments/assets/a33ab9e3-4260-4559-a594-b447f3281d48" alt="p avg" width="400" height="200">   

