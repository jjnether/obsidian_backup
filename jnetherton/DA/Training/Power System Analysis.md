Brian Johnson

Easier to work with phasor domain than time domain
We assume frequency is the same across the system

synchrophasors - Time synchronized phasor measurements


Sinusoidal signal: $r(t)=R_mcos(\omega t+\theta)$
- $R_m$ is peak value
Polar: $R\angle \theta$
- $R=\frac{R_m}{\sqrt{2}}$
Cartesian: $A+jB$
Exponential: $Re^{j\theta}$
Euler's trig identity: $R(cos\theta + jsin\theta)=Re^{j\theta}$
- $A=Rcos\theta$
- $B=Rsin\theta$
- $R=\sqrt{A^2+B^2}$
- $\theta=tan^{-1}\frac{B}{A}$

###### Phasor Arithmetic
- Addition and subtraction easier in polar
	- $(A+jB)+(C+jD)=(A+C)+j(B+D)$
	- $(A+jB)-(C+jD)=(A-C)+j(B-D)$
- Multiplication, division, and exponents easier in polar
	- $A\angle B(C\angle D)=A(C)\angle (B+D)$
	- $\frac{A\angle B}{C\angle D}=\frac{A}{C} \angle (B-D)$
	- $(A\angle B)^{n}=A^{n}\angle B(n)$

Balanced 3$\phi$ system
- All average power components are equal
- double frequency terms sum to 0


###### Complex Power
$\vec S=\vec V \vec I^{*}$
- `* means complex conjugate`
- $\vec V = |V|e^{j\theta_V}$
- $\vec I^{*}=|I|e^{-j\theta_I}$
$S=V_{rms}I_{rms}cos(\theta_V-\theta_I)+jsin(\theta_V-\theta_I)$
$S=P+jQ$
- S: Complex Power (Volt-Amperes, VA)
- P: Real Power (Watts, W)
- Q: Reactive Power (Volt-Amperes Reactive, VAR)
	- Energy needed to support electric and magnetic fields
		- $v(t)$ proportional to electric field
		- $i(t)$ proportional to magnetic field
power factor: $pf=\frac {P}{Q}$

$P=|S|cos\theta$
- $\theta = \theta_V-\theta_I$
- unity power if $cos\theta=1$

Inductive Load ($jQ$)
- lagging power factor
- power triangle in first quadrant (positive)
- consuming reactive power

Capacitive Load ($-jQ$)
- leading power factor
- power triangle in fourth quadrant (negative)
- supplying reactive power

power factor depends on wording
- 0.9 leading (supply Q)
- 0.9 lagging (consume Q)

measure I,V -> calculate P,Q

Balanced system if:
- Equal voltage magnitude on each phase
- Equal current magnitude on each phase
- 120$\degree$ phase shift between adjacent phase voltage and currents
###### Wye
![[Pasted image 20240813133021.png]]
- line-to-line voltage and line-to-neutral voltage
- phase currents $=$ line currents
$\vec S_{3ph}=\vec V_{AG} \vec I^{*}_A+\vec V_{BG} \vec I^{*}_B+\vec V_{CG} \vec I^{*}_C$
- or if balanced system:
	- $\vec S_{3ph}=3\vec V_{AG} \vec I^{*}_A$
	- Only have to do math on single phsae
- $V_{AG}=V_{AN}$ in normal operation
- $V_{AB}=V_{AG}-V_{BG}$
 - $V_{AB}=\sqrt 3 V_{AG}\angle 30 \degree$
	 - negative sequence rotation would cause a negative phase shift

###### Delta
![[Pasted image 20240813132941.png]]
- note that for this diagram $I_{BA}=I_a$ and $V_{AB}=E_{AB}$
- line-to-line voltage only
	- phase voltage $=$ line voltage
- line currents and phase currents
	- phase current $\neq$ line current
$\vec S_{3ph}=\vec V_{AB} \vec I^{*}_{AB}+\vec V_{BC} \vec I^{*}_{BC}+\vec V_{CA} \vec I^{*}_{CA}$
- or if balanced system:
	- $\vec S_{3ph}=3\vec V_{AB} \vec I^{*}_{AB}$
- $I_A=I_{AB}-I_{CA}$
- $I_A = \sqrt3 I_{AB}\angle 30 \degree$
	- negative sequence rotation would cause a negative phase shift

Horsepower
- .746 KW=1 HP

###### Per Unit
Usually nominal voltage is 1pu

Transformer turns:
- $V_H=nV_L$
	- $n=\frac {\#turnsHV} {\#turnsLV}$
- $I_H=\frac{1}{n}I_L$
- $Z_H=n^2Z_L$
- transformer turns ratios = 1 in per unit domain

Per Unit quantity = Actual (has angle)/Base (no angle)

###### Transformer Polarity and Phase Shift
- Delta-Delta
	- No neutral unless 4-wire secondary is used
	- All winding insulation must withstand L-L voltage
- Wye-Wye
	- MUST have at least one side grounded to be stable
	- Allows propagation of triplen harmonics if both sides grounded
		- If one side ungrounded, triplen harmonics will be blocked, but will cause voltage distortion instead
- Delta-Wye
	- Blocks balanced triplen harmonics
		- Triplen harmonics
			- odd multiples of 3rd phase harmonics (3rd, 9th, 15th, etc.)
		- Harmonic only circulates in the delta circuit, doesn't go beyond it
	- Provides neutral to accommodate single-phase loads
	- Provide ground fault current phase
	- Introduces phase shift
	- ANSI standard- Vln on HV side leads Vln on LV side by 30 degrees
	- IEC notation: Yd or Dy (upper case letter shows HV side) — follow by clock position

- 2nd harmonic magnetizing inrush
	- transformer draws large current to try to get flux to match applied voltage (mismatch due to hysteresis loop)
	- if doing a 3-ph close on a transformer, each phase will have different magnitude of 2nd harmonic content due to different voltage levels
		- this unbalance will pass some 2nd harmonic content to the line
- Grounding transformers only provide a path for zero-sequence current
- Metering CT's are very accurate, but only for a small range above nominal (then it saturates)
- Protection CT's are not as accurate, but have higher ceiling of saturation, so they can detect faults that are much higher levels than nominal
###### Symmetrical Components
- Balanced 3-ph circuits are analyzed on a single-phase basis
- For unbalanced 3-ph circuits, the unbalanced phasors must be resolved into balanced components so the single-ph equivalent method can be used
	- then add by linear superposition
- Voltages must be line to ground voltages
- Currents must be line currents

	![[Pasted image 20240814110033.png|200]]
	![[Pasted image 20240814110604.png|200]]

- Residual current: $I_R=3I_0=I_A+I_B+I_C$

Impedance diagrams
- For motors, you only include the source if you want to simulate the fact that it produces current for a short time until it winds down
- For calculating the thevenin equivalent impedance Xeq at point A:
	- B---X1---A---X2---X3---B (where B is bus and X's are impedances)
	- Xeq=X1||(X2+X3)
- When going from positive to negative sequence diagram, simply short sources
- When going from negative to zero sequence diagram:
	- You need to know the configuration (delta, wye with/without neutral, wye with Xn for neutral connection) for each side
	- If Delta
		- Open circuit and short to reference bus on the device side
	- If Wye (no neutral)
		- Open circuit on that side
	- If grounded Wye
		- Do nothing
	- If grounded wye with Xn for neutral
		- Multiply Xn by 3 and add to device impedance only
	
![[Pasted image 20240814162543.png|400]]

###### Fault Current
- Breakers depend on naturally occurring current zeroes to clear a fault
	- So a fault with a large enough DC offset that it doesn't cross zero can cause problems
		- They have to put in logic for it to wait to interrupt until it finally crosses zero. Otherwise, it will just arc across the contacts
- Maximum Fault Current
	- Zero fault impedance ($Z_F=0$)
	- All generation online
	- Maximum load level
- Minimum Fault Current
	- 25$\ohm$ to 40$\ohm$ fault impedance
		- many utilities have standard values they apply
	- Minimum generation online
	- Minimum load level
- Short Circuit Fault
	- Short one or more phases either to ground or another conductor

Fault types:
- For Impedances, be sure to use the proper angle
	- If it's only inductive reactance, than would simply be $\angle 90 \degree$
- After finding the sequence voltages and currents, the method of diving into each network to find the specific voltage and current at the relay is the same no matter what fault type
- Three-ph fault (tied together or to ground)
	- Only $I_1$ is used ($I_0=I_2=0$)
	- $I_A=\frac{V_f}{Z_1+Z_F}$
		- $V_f$ is Thevenin voltage (prefault)
		- $Z_1$ is Thevenin impedance
		- $Z_F$ is fault impedance (usually resistive)
	![[Pasted image 20240815114815.png|150]]
- Single line to ground fault (A-ph)
	- $I_B=I_C=0$ (fault current)
	- $I_0=I_1=I_2$ (all sequence networks  in series)
	- $I_0=\frac{V_f}{Z_1+Z_2+Z_0+3Z_F}$
	![[Pasted image 20240815114908.png|175]]
- Double line to ground fault (B-ph and C-ph)
	- $I_A=0$ (fault current)
	- $V_B=V_C=0$ (phases tied to ground)
	- $V_0=V_1=V_2$ (sequence networks are in parallel)
	![[Pasted image 20240815115024.png|400]]
- Line to Line Faults (B-ph to C-ph)
	- $I_A=0$ (fault current)
	- $V_1=V_2$ (positive and negative sequence)
	- $I_1=\frac{V_F}{Z_1+Z_2+Z_F}$
	- $I_2=-I_1$
	- $I_0=0$
	![[Pasted image 20240815115122.png|300]]

###### Series Faults - Open Circuit Conditions
- Possible causes
	- Broken conductor
	- Intentional single pole tripping
	- Breaker failure to trip (two poles open)
	- Breaker failure to close (one pole open)
- Requires two port Thevenin equivalent circuit

- One Line Open
	![[Pasted image 20240815133228.png|400]]

- Two Line Open
	![[Pasted image 20240815133312.png|400]]