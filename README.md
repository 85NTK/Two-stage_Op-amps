# Two-stage_Op-amps
Design of two-stage Op-amps using CMOS 180NM technology
## Specifications
Uses 180nm CMOS technology, the channel length is  $0.5µm$, load capacitor is $C_L = 10pF$
|$A_v>3000V/V$|$V_{DD}=0.9V;V_{SS}=-0.9V$|$GB=10MHz$|$SR>12V/µs$|
|-------------|-------------------------|----------|----------|
|$60°$ phase margin|$V_{out}range=-0.5V to 0.5V$|$ICMR=-0.5V to 0.5V$|$P_{diss}≤3mW$|
## Calculations
### Extract Parameters
![NMOS_schematic](/FLOWCHART/NMOS_schematic.png)
![NMOS_Simulation](/FLOWCHART/NMOS_Simulation.png)
#### NMOS
- $V_{DS1}=1.4003257V, I_{D1}=1.1182828mA$
- $V_{DS2}=1.5996743V, I_{D2}=1.131001mA$
- $λ_N=(I_{D2}-I_{D1})/(I_{D1}.V_{DS2}-I_{D2}.V_{DS1})=0.062$
- $λ_P=(I_{D2}-I_{D1})/(I_{D1}.V_{DS2}-I_{D2}.V_{DS1})≈0.08$









