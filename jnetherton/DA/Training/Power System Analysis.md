Brian Johnson

Easier to work with phasor domain than time domain
We assume frequency is the same across the system

synchrophasors - Time synchronized phasor measurements


Sinusoidal signal: $r(t)=R_mcos(\omega t+\theta)$
Polar: $R\angle \theta$
- $R=\frac{R_m}{\sqrt{2}}$
Cartesian: $A+jB$
Exponential: $Re^{j\theta}$
Euler's trig identity: $R(cos\theta + jsin\theta)$
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
- phase voltage $=$ line voltage
- phase current $\neq$ line current

Wye
![[Pasted image 20240813101504.png]]