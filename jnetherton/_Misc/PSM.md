Motor Power Supply: B54020023000

6 ohm load?

-   100 W goal to simulate steady state



Only Comb wave (no ring wave)



Variable load box



Is it dumb to test everything on two different PSM's? (Jason wanted sample size of 2)



For surge, when do I do impulses? (0 degrees, 90, 180, 270?)



Do I do transversal testing for comb wave too?





<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 70%" />
</colgroup>
<thead>
<tr class="header">
<th>Extreme Temp</th>
<th><p>IEC 60068-2-1</p>
<p>IEC 60068-2-2</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Damp Heat</td>
<td><p>IEC 60068-2-30:2005 (what is 2005?)</p>
<p>IEC 60068-2-78 ???</p></td>
</tr>
<tr class="even">
<td>Salt Fog</td>
<td>ASTM B117-19</td>
</tr>
<tr class="odd">
<td>EMC</td>
<td><p>IEEE C37.90.1</p>
<p>IEEE C37.90.2</p>
<p>IEEE C37.90.3</p>
<p>IEC 61000-4-6</p>
<p></p>
<p>IEEE C62.41</p>
<p>IEC 61000-4-11 Section 7.2.11</p>
<p>G&amp;W Engineering Standard 210.001-14</p></td>
</tr>
</tbody>
</table>



![Machine generated alternative text: 4. Component Level Testing 4.1. Environmental 4.1.1. Extreme Cold • IEC 60068-2-1 Fifth Edition -1990 [EN 60068-2-1 Fifth Edition -1993] • Environmental testing, Part 2: Tests - Test Ad: Cold. Severity Level: 16 hours at 4.1.2.Dry Heat • IEC 60068-2-2 Fourth Edition- 1974 [EN 60068-2-2 Fourth Edition -1993] --- 400C • Environmental testing, Part 2: Tests - Test Bd: Dry heat. Severity Level: 16 hours at + 850C 4.1.3.Damp Heat • IEC 60068-2-30 • 48 Hours, 95% RH, 250Cto 550< 4.1.4.Transportation Vibration • ASTM 04169 Truck level Ill, 3 Hours 4.2. Electromagnetic Compatibility 4.2.1. Surge Withstand Capability Immunity • IEEE C37.go.1 • IEEE standard for surge withstand capability (SWC), tests for protective relays and relay systems associated with Electric Power Apparatus. • Severity Level: 2.5 kv peak common mode, 2.5kV peak differential mode oscillatory waveform, 4 kv at 2.5kHz and 5kHz fast transient waveform 4.2.2. Radiated Immunity • IEEE C37.90.2 • IEEE Standard for Withstand Capability of Relay Systems to Radiated Electromagnetic Interference from Transceivers • • Severity Level: 35 V/m, 8MOOOMHz 4.2.3. ESD • IEEE C37.90.3 • IEEE Standard Electrostatic Discharge Tests for Protective Relays • Severity Level: 15kV 4.2.4. Conductive Immunity • IEC 61000-4-6 Electromagnetic compatibility (EMC) - Part 4-6: Testing and measurement techniques - Immunity to conducted disturbances, induced by radio-frequency fields Severity Level: IOV ](Quick-Notes-PSM-image1.png){width="14.458333333333334in" height="13.770833333333334in"}

How to do these for verifying waves in surge testing?

![Machine generated alternative text: 54.2 Waveform validity tests The waveform validity tests shall be performed and aner each SWC test Clause 8, "ith tip results recorded and included uith the SWC test repolt. The tests described in B2 are intended to veri$' that there is no major ilEuIation breakdouu damage, or test system component failue that rmy have cccu_ned during the physical test setup, test or prolonged l_nsmunent storage. The valiåty tests shall include: a) b) c) d) Measuring system test Oscillatory SWC test generator 01211 circuit voltage wavefonn test Fast transient SWC test generator circuit voltage wate%nn test Measurement nzthods different from those described in the Annex B are acceptable, as long as tip sanz level of and the same paranrters are used to docun_lent the results. ](Quick-Notes-PSM-image2.png){width="11.791666666666666in" height="4.375in"}



CHANGES:

-   No ring wave test (included in damped oscillatory)
-   Comb wave specs (5 surges each polarity, not 10)
-   93% humidity (not 95) and damp heat temp 40 C (not 55)
-   For EFT, not sure where the 2.5 kHz came from
-   For ESD, add specifics for test voltage (8 kv for contact, 15 kv for air)



Voltage dips:

0% - 5 cycles (83 ms) (10 cycles - 167ms I could hear PSU's switching) (when switched off, voltage goes down by about .5 V)

40% - 200ms

70% - 500ms



IEC 60255-26



Recording PSU 1

Looked for voltage falling below 21 V with a trigger

![Machine generated alternative text: 5. System Level Testing The following testing is to be done on either a full control cabinet assembly or an equivalency of components to deem a full system. This should include a the very least the appropriate number of UG Power Supplies G&W PN 354020023000 required based on share module design. 5.1. Electromagnetic Compatibility 5.1.1. AC Surge Immunity • IEEE C62.41 • IEEE Recommended Practice for Surge Voltages in Low-Voltage AC Power Circuits • Combination Surge Wave: 0 1.2x50 / 8x20 Combination Wave o Severity Level: 4kV peak, 2 Ohm source. 10 surges each polarity, I-minute repetition. Applied at 00, 90', 1800, and 270. Ring Wave: 0 100 kHz Damped Ring wave o Severity Level: 4kV peak, 12 Ohm source. 10 surges each polarity, I-minute repetition. Applied at 00, 900, 1800, and 270. 5.1.2. AC Input Power Interruptions • IEC 61000-4-11 Section 7.2.11 • Testing and measurement techniques - Voltage dips, short iptgrrup.giprl>. and voltage variations immunity tests 0 0%0.5 cycles (minimum) 0 40% 12 cycles 0 30 cycles o Note above to be tested with and without batteries to determine functionality limits 5.1.3. Low Frequency Transients G&W Engineering Standard 210.001-14 Power Supply Low Frequency Transients Test 120V / 240V nominal input tests o Frequencies: 300Hz, 1kHz o Voltages: 120V nominal: 340Vpeak, 3 cycles 240V nominal: 680Vpeak, 3 cycles 10 transients each configuration 1 minute between repetitions ](Quick-Notes-PSM-image3.png){width="13.645833333333334in" height="11.895833333333334in"}

Tvs diode or MOV's



NOTES:

We were originally testing to the Ad and Bd testing (not powered throughout), but since the inconsistent PSM failures, starting with ramping back to ambient from cold, we'll keep it powered throughout (Ae and



