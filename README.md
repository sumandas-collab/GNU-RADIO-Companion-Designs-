# GNU-RADIO-Companion-Designs
This includes the designs I have made in GNU Radio Companion and the .grc files along with it

# Introduction
GNURadio is an open-source software development toolkit used for implementing software
defined radio and digital signal processing systems. It provides signal processing blocks that
can be connected to form flowgraphs for communication system simulations.
GNU Radio Companion (GRC) is a graphical interface that allows users to visually
connect blocks such as signal sources, filters, modulators, and sinks to build signal processing
systems.
In this experiment several tasks were performed including dual tone generation, peak
detection, filter tap implementation using FIR filters, and QAM modulation. The behavior
of signals and systems was analyzed using time plots, frequency plots, constellation diagrams,
and eye diagrams

# 1 Task 1: Dual Tone Generator
# 1.1 Aim / Objective
To generate a dual-frequency audio signal, add noise to the signal, and dynamically control
the frequencies, noise level, and signal amplitude using slider widgets.
1.2 Theory
A dual tone signal is obtained by adding two sinusoidal signals with different frequencies.
[ x(t) = A1cos(2πf1t) + A2cos(2πf2t)]
where
• f1 and f2 represent the two frequencies
• A1 and A2 represent the amplitudes
Noise can be added to the signal using Gaussian noise:
[ y(t) = x(t) + n(t) ]
where n(t) represents random Gaussian noise.
In GNU Radio, two signal sources are used to generate the tones, and a noise source is
added using an adder block.
# 1.3 Design / Flow Graph
<img width="1310" height="653" alt="1  Dual tone generator design" src="https://github.com/user-attachments/assets/5cae0401-d89a-4626-94b7-639059300164" />
# Figure 1: GNU Radio Flowgraph for Dual Tone Generation
# 1.4 Results
<img width="1914" height="1011" alt="1  Dual tone generator result" src="https://github.com/user-attachments/assets/bf8832f2-a3df-4f0a-8607-21aaa531563c" />
Figure 2: Dual Tone Generator Output with Adjustable Sliders
The GUI includes sliders to dynamically control:
• Frequency of the first tone
• Frequency of the second tone
• Signal amplitude (volume)
• Noise amplitude
Changing these parameters modifies the generated audio signal in real time.
# 1.5 Observations
• The generated signal contains two superimposed sinusoidal tones.
• Increasing noise amplitude introduces distortion in the signal.
• Changing frequency sliders alters the pitch of the tones.
• The volume slider controls the output amplitude of the signal.
