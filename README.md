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
# 1.2 Theory
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
Figure 1: GNU Radio Flowgraph for Dual Tone Generation.

# 1.4 Results
<img width="1914" height="1011" alt="1  Dual tone generator result" src="https://github.com/user-attachments/assets/bf8832f2-a3df-4f0a-8607-21aaa531563c" />
Figure 2: Dual Tone Generator Output with Adjustable Sliders.

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


# 2 Task 2: Peak Detector
# 2.1 Aim / Objective
To generate a sawtooth waveform with noise and detect its peaks using a peak detector
block.

# 2.2 Theory
Apeak detector identifies local maxima in a signal by comparing each sample with neighbor
ing samples. It uses parameters such as threshold factor, look-ahead samples, and smoothing
coefficient.
The input signal can be represented as:
[ x(t) = Sawtooth(t) + n(t) ]
The peak detector identifies points where the signal amplitude reaches a maximum within
a specified window.

# 2.3 Design / Flow Graph
<img width="1247" height="637" alt="2  Peak detector design" src="https://github.com/user-attachments/assets/d00b1f0b-bac2-4541-9d72-83317833a592" />
Figure 3: Peak Detector Flowgraph.

# 2.4 Results
<img width="1914" height="978" alt="2  Peak detector results" src="https://github.com/user-attachments/assets/04eec06c-9dd7-4a1d-8385-5f6c8d5bca08" />
Figure 4: Peak Detection Result
The time plot shows three signals:
• Blue curve– original sawtooth waveform
• Red spikes– detected peaks
• Green curve– threshold level used for detection.

# 2.5 Observations
• The peak detector successfully detects peaks of the sawtooth waveform.
• Red spikes correspond to the maximum points in each cycle.
• The threshold parameter controls the sensitivity of detection.
• Noise slightly distorts the waveform but peaks remain detectable.

# 3 Task 3: Filter Tap Design
# 3.1 Aim / Objective
To generate a CW signal with noise and design filter taps using FIR filters. Low-pass,
high-pass, and band-pass filters are implemented to study their frequency responses.
# 3.2 Theory
A Finite Impulse Response (FIR) filter processes signals using a finite set of coefficients
called filter taps.
[ y[n] = N−1
k=0 
h[k]x[n − k]]
where
• h[k] represents filter tap coefficients
• x[n] is the input signal
• N is the number of taps
Different filters can be designed by modifying the taps.
Low Pass Filter (LPF) allows low frequency components and attenuates higher fre
quencies.
High Pass Filter (HPF) removes low frequencies and allows higher frequencies.
Band Pass Filter (BPF) allows signals within a specific frequency band.
# 3.3 Design / Flow Graph
<img width="1476" height="586" alt="3  Filter taps_FIR filter" src="https://github.com/user-attachments/assets/e3ae13fc-a9ad-4f95-8f81-f2271ed18fbf" />
Figure 5: Filter Tap Flowgraph.

# 3.4 Results (FIR Filter)
<img width="1914" height="972" alt="3  Filter taps using FIR filters result" src="https://github.com/user-attachments/assets/b8a8f160-e40e-47c9-933c-f75244dda3ac" />
Figure 6: Frequency Response of FIR Filter.

In the frequency spectrum:
• Blue curve represents the filter response.
• Red curve represents the noisy input signal.
• Sharp peaks represent sinusoidal signal components.

# 3.5 Extension: LPF, HPF and BPF
<img width="1366" height="662" alt="5  Filter Taps_LPF_HPF_BPF" src="https://github.com/user-attachments/assets/690dc877-b6b0-4322-9c74-ef1930549433" />
Figure 7: Flowgraph for LPF, HPF and BPF
<img width="1908" height="988" alt="5  Filter taps LPF HPH BPF result" src="https://github.com/user-attachments/assets/04d78c68-80dd-4acb-b445-467d17dfdc2e" />
Figure 8: Frequency Response of LPF, HPF and BPF.

The spectrum shows:
• Blue curve (Data 0)– Output of the Low Pass Filter (LPF), which allows low frequency
components while attenuating higher frequencies.
• Red curve (Data 1)– Output of the Band Pass Filter (BPF), which passes only a
specific band of frequencies around the center frequency.
• Green curve (Data 2)– Output of the High Pass Filter (HPF), which suppresses low
frequencies and allows higher frequency components.
• Black curve (Data 3)– Spectrum of the original noisy input signal before filtering.

# 3.6 Observations
• LPF allows low frequency components to pass.
• HPF removes low frequency components.
• BPF allows only a selected band of frequencies.
• Noise outside the passband is suppressed by the filters.

# 4 Task 4: QAM Modulation
# 4.1 Aim / Objective
To generate a QAM signal, introduce channel impairments, and observe the constellation
diagram and eye diagram.

# 4.2 Theory
Quadrature Amplitude Modulation (QAM) transmits information using both amplitude and
phase variations of a carrier.
[ s(t) = I(t)cos(2πfct) − Q(t)sin(2πfct)]
where
• I(t) = in-phase component
• Q(t) = quadrature component
In 4-QAM,theconstellation contains four symbol points representing two bits per symbol.

# 4.3 Design / Flow Graph
<img width="1616" height="624" alt="4  QAM" src="https://github.com/user-attachments/assets/3e6f0337-f8c5-482c-8bfc-e2153374b9e1" />
Figure 9: QAM Flowgraph.

# 4.4 Results
<img width="1894" height="993" alt="4  QAM result" src="https://github.com/user-attachments/assets/8b0d38dc-614e-4a26-9dae-a5155785ce5d" />
Figure 10: QAM Constellation and Eye Diagram
Observed plots:
• Time domain signal.
• In-phase and Quadrature signals.
• Constellation diagram showing four symbol points.
• Eye diagram representing symbol timing.

# 4.5 Observations
• Theconstellation diagram clearly shows four clusters corresponding to 4-QAM symbols.
• Channel impairments distort the constellation points.
• Eye diagrams illustrate symbol timing and noise effects.

# Conclusion
In this experiment, various signal processing operations were implemented and analyzed
using GNU Radio Companion. A dual tone generator was successfully designed by combining
two sinusoidal signals and adding Gaussian noise, while slider widgets enabled real-time
control of frequency, amplitude, and noise level. A peak detector was implemented to identify
the peaks of a noisy sawtooth waveform, demonstrating how signal maxima can be detected
using threshold and look-ahead parameters.
