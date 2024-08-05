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



