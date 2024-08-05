# Two-stage_Op-amps
Design of two-stage Op-amps using CMOS 180NM technology
## Specifications
Uses 180nm CMOS technology, the channel length is  $0.5µm$, load capacitor is $C_L = 10pF$
|$A_v>3000V/V$|$V_{DD}=0.9V;V_{SS}=-0.9V$|$GB=10MHz$|$SR>12V/µs$|
|-------------|-------------------------|----------|----------|
|$60°$ phase margin|$V_{out}range=-0.5V to 0.5V$|$ICMR=-0.5V to 0.5V$|$P_{diss}≤3mW$|
## Schematic
![Two-stage_Op-amps_schematic](/FLOWCHART/Two-stage_Op-amps_schematic.png)
## Calculations
### Extract Parameters
![NMOS_schematic](/FLOWCHART/NMOS_schematic.png)
![NMOS_Simulation](/FLOWCHART/NMOS_Simulation.png)
- $V_{DS1}=1.4003257V, I_{D1}=1.1182828mA$
- $V_{DS2}=1.5996743V, I_{D2}=1.131001mA$
- $λ_N=(I_{D2}-I_{D1})/(I_{D1}.V_{DS2}-I_{D2}.V_{DS1})=0.062$
- $λ_P=(I_{D2}-I_{D1})/(I_{D1}.V_{DS2}-I_{D2}.V_{DS1})≈0.08$
![NMOS_model](/FLOWCHART/NMOS_model.png)
- $ε_o=8,854.10^{-12}F/m$	
- $ε_r(SiO_2)=3,9$
- $T_{OX}=4,1.10^{-9}$
- $C_{ox}=(ε_o*ε_r)/T_{OX} =8,4 .10^{-3}F/m^2$
#### NMOS
- $µ_n=U_0=280.5758609cm^2/VS$
- $K_{n'}=µ_nC_ox=236μA/V^2$
- $K_n=1/2C_{ox}µ_n=118μA/V^2$
- $V_{TN}=V_{TH0}=0.393 V$
- $λ_N=0.062 V^{-1}$
#### PMOS
![PMOS_model](/FLOWCHART/PMOS_model.png)
- $µ_n=U_0=116.1690772cm^2/VS$
- $K_{n'}=µ_nC_ox=98μA/V^2$
- $K_n=1/2C_{ox}µ_n=49μA/V^2$
- $V_{TN}=V_{TH0}=-0.404V$
- $λ_N=0.08V^{-1}$
### Calculate the parameters according to the theory
1. From the phase margin $60^°$ and the $C_L$ capacitor value, calculate the minimum value of the capacitor $C_c$
- $C_c>22/10×C_L⇒C_c>22/10×10pF=2.2pF$
2. Choose $C_c=3p$. Calculate $I_5$ from $SR$ and $C_c$
- $I_5=SR.C_c=(12×10^6)(3×10^{-12})=36μA$
3. Use $ICMR$ calculate $(W/L)_3$
- $(W/L)_3=(W/L)_4$
- $=I_5/(K_{p3'}[V_{DD}-V_{in}(max)-|V_{T03}|(max)+V_{T1}(min)]^2)$
- $=(36×10^{-6})/(98×10^{-6}×[0.9-0.5-0.484+0.313]^2)=7$
4. Calculate the value $(W/L)_1$ to reach $GB=10MHz$
- $g_{m1}=GB.2π.C_c$
- $=(10×10^6)(2π)(3×10^{-12})=188.5μS$
- $(W/L)_1=(W/L)_2$
- $=g_{m1}^2/(K_{n1'}I_5)$
- $=(188.5×10^{-6})^2/(236×10^{-6}×36×10^{-6})=4.18$
5. Calculate $V_{DS5}(sat)$ from $ICMR$ from which $(W/L)_5$
![(WL)5](/FLOWCHART/(WL)5.png)
6. Calculate $(W/L)_6$
![(WL)6](/FLOWCHART/(WL)6.png)
7. Calculate $I_6$ from $g_{m6}$ value
![I6](/FLOWCHART/I6.png)
8. Calculate $(W/L)_7$ based on $I_6/I_5$
![(WL)7](/FLOWCHART/(WL)7.png)
9. Checking the parameters again
![CheckingParametersAgain](/FLOWCHART/CheckingParametersAgain.png)
## Simulation
### Schematic
![gainWaves](/FLOWCHART/gainWaves.png)
### Simlation results
#### Gain
![gainFormula](/FLOWCHART/gainFormula.png)
![gainWaves](/FLOWCHART/gainWaves.png)
![gainLog](/FLOWCHART/gainLog.png)
#### Gain Bandwidth
![gainBandWidth](/FLOWCHART/gainBandWidth.png)
- $GB= A_v×f_c$
- Taken at $0dB: A_v=1→GB=f_c$
- Take at the highest gain $(dB)$ minus $3dB:GB=A_v×f_{-3dB}$
- Example: $68 dB→A_v=10{68/20}$
#### Phase Margin
- Difference of 2 margins minus each other: Phase at $0dB-(-180^°)$ gain
![phaseMargin](/FLOWCHART/phaseMargin.png)
#### Slew rate
- Circuit Response
- Speed Adding a square wave (step) uses the regression property of the algorithm amplification circuit
![slewRate](/FLOWCHART/slewRate.png)
- Due to the response speed of the circuit, the output wave is jammed
- Measured in linear ramps, not curves
#### Power Dissipation
- Single source: $P_{diss}=(V_{DD}+|V_{SS}|)×(I_{Whole Circuit})
- Dual power: $P_{diss}=V_{DD}×(I_{whole circuit})
- Simulation: .meas Tran power AVG 2V(vn001)*Id(M5)
#### $V_{out} range$
$v_{out}=V_{out}+v_{out}$
$V_{DS}>V_{GS}-V_{th}$
![voutRange](/FLOWCHART/voutRange.png)
- Input signal is serrated wave (scan from -0.9V to 0.9V)
- The output signal is almost like a serrated wave, choose a linear segment to measure
## Assess
|PARAMETERS|SPECIFICATION|CALCULATE|SIMULATE|
|----------|-------------|---------|--------|
|$A_v$|$>3000V/V|$4532.3$|$1111.51|
|$GB$|$10MHz$|$10MHz$|$2.45MHz|
|$SR$|$>12V/μS$|$12V/μS$|$8.77V/𝜇S$|		
|$V_{out range}|$-0.5V→0.5V$|$−𝟎.𝟔𝟑𝟔𝑽→𝟎.𝟔𝟕𝟏𝑽$|$−𝟎.𝟔𝑽→𝟎.𝟔𝑽$ |	
|P_{diss}|$≤3mW$|$0.45mW$|$0.342mW$|
