Brian Johnson

Easier to work with phasor domain than time domain
We assume frequency is the same across the system

synchrophasors - Time synchronized phasor measurements


Sinusoidal signal: $r(t)=R_mcos(\omega t+\theta)$
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

Delta
![[Pasted image 20240813101011.png]]
- line-to-line voltage only
	- phase voltage $=$ line voltage
- line currents and phase currents
	- phase current $\neq$ line current


Wye
![[Pasted image 20240813101504.png]]
- line-to-line voltage and line-to-neutral voltage
- phase currents $=$ line currents

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
###### Wye 3ph calculations
$\vec S_{3ph}=\vec V_{AG} \vec I^{*}_A+\vec V_{BG} \vec I^{*}_B+\vec V_{CG} \vec I^{*}_C$
- or if balanced system:
	- $\vec S_{3ph}=3\vec V_{AG} \vec I^{*}_A$
	- Only have to do math on single phsae
- $V_{AG}=V_{AN}$ in normal operation
- $V_{AB}=V_{AG}-V_{BG}$
 - $V_{AB}=\sqrt{3}V_{AG}$

###### Delta 3ph calculations
$\vec S_{3ph}=\vec V_{AB} \vec I^{*}_{AB}+\vec V_{BC} \vec I^{*}_{BC}+\vec V_{CA} \vec I^{*}_{CA}$
- or if balanced system:
	- $\vec S_{3ph}=3\vec V_{AB} \vec I^{*}_{AB}$
- $I_{AB}=\sqrt{3}I_{A}$
- 