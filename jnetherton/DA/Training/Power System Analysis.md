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

###### Symmetrical Components
- Balanced 3-ph circuits are analyzed on a single-phase basis
- For unbalanced 3-ph circuits, the unbalanced phasors must be resolved into balanced components so the single-ph equivalent method can be used
	- then add by linear superposition
- Voltages must be line to ground voltages
- Currents must be line currents

![[Pasted image 20240814110033.png|200]]
![[Pasted image 20240814110604.png|200]]

- Residual current: $I_R=3I_0=I_A+I_B+I_C$
- 