# DSB-SC-AM-MODULATOR-AND-DEMODULATOR-USING-SCILAB-T1-M4-ODD
# DSB-SC-AM MODULATOR AND DEMODULATOR

## AIM

To write a program to perform DSBSC modulation and demodulation using SCI LAB and study its spectral characteristics.

---

## EQUIPMENTS REQUIRED

* Computer with i3 Processor
* SCI LAB

> **Note:** Keep all the switch faults in off position.

---

## ALGORITHM

### 1. Define Parameters:

* **Fs:** Sampling frequency.
* **T:** Duration of the signal.
* **Fc:** Carrier frequency.
* **Fm:** Frequency of the message signal.
* **Amplitude:** Maximum amplitude of the message signal.

### 2. Generate Signals:

* **Message Signal:** A sinusoidal signal that will be modulated.
* **Carrier Signal:** A high-frequency sinusoidal signal used for modulation.

### 3. DSBSC Modulation:

* **Modulated Signal:** Multiply the message signal by the carrier signal to produce the DSBSC signal.

### 4. DSBSC Demodulation:

* **Multiplication:** Multiply the modulated signal by the carrier signal to get the product of the message signal with itself (i.e., the original message signal plus high-frequency components).
* **Low-pass Filtering:** Apply a Butterworth low-pass filter to remove the high-frequency components and recover the original message signal.

### 5. Visualization:

Plot the message signal, carrier signal, DSBSC modulated signal, and the recovered signal after demodulation.

---
## CODE
clc;
clear;
close;

// Time
t = 0:0.00001:0.01;

// Message signal
Am = 1;
fm = 1000;
m = Am*sin(2*%pi*fm*t);

// Carrier signal
Ac = 1;
fc = 10000;
c = Ac*cos(2*%pi*fc*t);

// DSB-SC Modulation
dsbsc = m .* c;

// Coherent Demodulation
demod = 2 * dsbsc .* c;

// Low Pass Filter
fc_lp = 2000;
[b,a] = iir(5,'lp','butt',[fc_lp/(1/(2*0.00001)) 0],[]);
output = flts(demod,b,a);

// Plot Message Signal
subplot(4,1,1);
plot(t,m);
xlabel("Time (s)");
ylabel("Amplitude");
title("Message Signal");

// Plot Carrier Signal
subplot(4,1,2);
plot(t,c);
xlabel("Time (s)");
ylabel("Amplitude");
title("Carrier Signal");

// Plot DSB-SC Signal
subplot(4,1,3);
plot(t,dsbsc);
xlabel("Time (s)");
ylabel("Amplitude");
title("DSB-SC Modulated Signal");

// Plot Demodulated Signal
subplot(4,1,4);
plot(t,output);
xlabel("Time (s)");
ylabel("Amplitude");
title("Demodulated Signal");
## PROCEDURE

* Refer Algorithms and write code for the experiment.
* Open SCILAB in System.
* Type your code in New Editor.
* Save the file.
* Execute the code.
* If any Error, correct it in code and execute again.
* Verify the generated waveform using Tabulation and Model Waveform.

---

## TABULATION

<img width="1486" height="856" alt="image" src="https://github.com/user-attachments/assets/de921aa8-dc62-4d78-8ab6-e91b7fe0a227" />


## MODEL GRAPH

<img width="1010" height="973" alt="image" src="https://github.com/user-attachments/assets/07d1031a-8248-40c4-818c-d81386d3032a" />

## OUTPUT
<img width="1167" height="615" alt="image" src="https://github.com/user-attachments/assets/7d27e23e-7466-4088-899f-f83d0a5c542d" />


## RESULT
Successfully performed DSBSC modulation and demodulation using SCI LAB.
