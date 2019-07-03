## Started 07/03/2019
## These are notes by Eric Graves taken while reading through "Audio Power Amplifier Design Handbook" by Douglas Self, 3rd ed.
### Most of these will be quotes directly from the text, with this document being for my own personal use while studying.

# Chapter 1 : Introduction and General Survey

### Motivation: 
The author provides a list of reasons to motvate the study of solid-state amplifier design, as he found these areas lacking in 2002.
- The need to balance input pair to prevent second-harmonic generation.
- The demonstraction of how beta-enhancement transistor increases the linearity and reduces the collector impedance of the VA stage.
- Why do BJT output stages distort more into 4 Ohm than 8 Ohm loads?
- In typical BJT output stage, quiescent current (IsubQ) is of little importance. Instead, function is driven by the voltage difference between the Emitters. 
- Power FETs are less linear in their behavior tha bipolar output devices (although seen as having superior linearity).
- DIstortion in amplifiers mainly comes from avoidable problems (induction in supply-rail currents, poor power-supply rejection (PSRR)) rather than the amplifier itself.
- Misunderstanding the source of square-wave ringing (often misatributed to transient response of amplifier into capaitive load), where this usually comes from the output inductor ringing with the capacitive load.

This book is focused more on enumerating current techniques rather than motivating the creation of new amplifier designs:
- Existing data focuses on small-signal MOSFET behavior (i.e. CMOS), and how it differs from BJT behavior. Ignoring the potential for CMOS behavior to be changed by manipulating device dimensions, etc.. 
	- This has changed over the years, as I saw in EE338L/EE384M : Analog Design of ICs now focuses on data-driven approaches (such as gm/id) to get desired behavior. However, my experinence with these was very limited in its power scope.
- CMOS op-amp design focuses on transconductance amplifiers compensated with large capacitance across the output, which is not promising for audio appications.
- Op-amp common-mode (CM) performance of an input stage is not relevant to power amplifier design.
- Circuit techniques that use matching and minimize fab costs (i.e. making a single transistor out of multiple transistors in parallel/series, and thendesigning chips where all channel widths are integer-related) are not as relevant to power amplifier design as to other areas.
- Limited space for capacitors/transistors in IC design is not an issue for power amplifiers.

Author will propose a design methodology for an amplifier designed for a specific negative-feedback factor at a given frequency, and somewhat allows the prediction of distortion performance. 

### Misinformation
The author covers what he sees as the largest areas of misinformation in the audio world.

#### Subjectivism
- Objective meausrements of perforamnce are less important than subjective measurements when listening to a speaker.
- Current objective tests fail to fully account for the sources of sound degradation in amplifiers, and can be ignored in favor of personal opinion.

#### Limits of Human Hearing
- Smallest detectable step-change in amplitude is ~0.3dB for a pure tone, more realistically 0.5-1.0dB (~10% change).
- Smallest detectable step change in frequency is about 0.2% in the band between 500Hz and 2kHz, which is where the ear is most sensitive.
- Least detectable Total Harmonic Distortion (THD) is not well defined. If mostly low-harmonics, estimate ~1%. Otherwise, estimate ~0.3% as a maximum.
- Interchannel crosstalk is not detectable until 20dB, well beyond the limits of sensible design.
- Limits of Phase and Group Delay are not well defined, but they should be kept to a minimum.

#### Subjectivist Claims with no Scientific Backing:
- "Sinewaves are steady-state signals and thus too easy a test for amplifiers, when compared to complexities of music."
	- Ridiculous in that it assumes that an amplifier "thinks" about the signal it is amplifying. Don't confuse waveshape with frequency, of course a sine wave would be swept across the spectrum to analysize amplifier behavior.
- "Capacitors create unmeasurable distortion"
	- These effects can be contributed to previously-known phenomena: dielectric absorbtion, series resistance, etc.
- "Cumilative deterioration of cables due to signals passed in routine use"
	- No evidence that electrical signals within defined use cases cause deterioration.
- "Tone controlls set to flat cause audible deterioration. Often blamed on phase-shift"
- "Power supply design has a subtle effect on sound, outside of ripple injection and other ordinary concerns"
	- Any good power supply will be designed to be intolerant to imperfections at its input.

PAGE 22