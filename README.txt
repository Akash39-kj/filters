Analog Signal Conditioning for Robust 6 kHz Signal Extraction
SynthetiX’26 Electrical Stream Hackathon

This project implements a purely analog signal conditioning circuit designed to extract a 6 kHz usable signal from a noisy composite sensor output in an industrial environment.

The design was developed as part of the SynthetiX’26 Electrical Stream Challenge, where digital processing techniques were strictly prohibited.

Problem Statement

Modern autonomous and industrial systems often operate in electrically hostile environments containing interference from switching power electronics, RF emitters, and broadband electromagnetic noise.

In this challenge, a black-box sensor module produces a composite analog signal containing:

Component	Frequency	Description
Component A	600 Hz	Low frequency drift
Component B	6 kHz	Usable signal
Component C	18 kHz	Structured interference
Component D	55 kHz	High frequency interference
Component E	Broadband	White noise

The goal is to design an analog-only signal conditioning circuit that:

Extracts the 6 kHz usable signal

Suppresses interference and noise

Maintains stable and repeatable operation

Provides manual tuning capability

Constraints:

No DSP

No microcontrollers

No programmable ICs

Only analog components allowed

Design Overview

The circuit uses a multi-stage analog filtering architecture to progressively suppress unwanted frequency components while preserving the useful signal band.

Signal Processing Flow
Black-box input
      │
Input Buffer
      │
High-Pass Filter (removes 600 Hz drift)
      │
Twin-T Notch / Frequency Shaping Stage
      │
Low-Pass Interference Suppression
      │
Manual Adaptation (Potentiometer tuning)
      │
Conditioned Output (6 kHz dominant)
Key Design Blocks
Input Buffer

A voltage follower isolates the 50 Ω source impedance of the black-box signal source from the filtering stages.

This ensures:

high input impedance

low output impedance

minimal signal distortion

High-Pass Filter

The high-pass stage removes the 600 Hz low-frequency drift component while preserving the useful signal band around 6 kHz.

Twin-T Notch / Frequency Shaping Stage

A Twin-T network provides targeted rejection of unwanted interference in the mid-frequency region.

This stage improves separation between the usable signal and structured interference.

Low-Pass Interference Suppression

Cascaded low-pass filters attenuate higher-frequency components including:

18 kHz structured interference

55 kHz high-frequency disturbance

broadband noise

Manual Adaptation Interface

A 100 kΩ potentiometer allows continuous tuning of the circuit response.

This satisfies the challenge requirement for:

smooth adjustment

predictable behavior

repeatable calibration

Optimal calibration occurs near:

Rknob ≈ 90 kΩ
Simulation Results

Simulation was performed using LTspice.

The conditioned output spectrum shows clear dominance of the 6 kHz signal.

Frequency	Output Level
600 Hz	-59.14 dB
6 kHz	-10.3 dB
18 kHz	-26.3 dB
55 kHz	-70.89 dB
Suppression Achieved
Interference	Suppression Relative to 6 kHz
18 kHz interference	~16 dB
600 Hz drift	~49 dB
55 kHz interference	~60 dB