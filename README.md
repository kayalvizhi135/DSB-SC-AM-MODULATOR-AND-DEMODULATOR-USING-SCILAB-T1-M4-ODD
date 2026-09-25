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

## PROGRAM

Am = 9.2;   

Ac = 18.4;

fm = 515; 

fc = 5150;

fs = 51500; 

T = 0.05;       

// Time vector

t = 0:1/fs:T;

// Message signal

m = Am*cos(2*%pi*fm*t);

// Carrier signal

c = Ac*cos(2*%pi*fc*t);

// DSB-SC modulation

dsb_sc = m .* c;

// Coherent demodulation

demod = dsb_sc .* c;

// Low-pass filter

fc_lpf = 300;

Wn = 2*%pi*fc_lpf/fs;

// FIR low-pass filter

N = 101;

h = ones(1,N)/N;

// Apply filter

recovered = convol(demod,h);

// Adjust time vector

t_rec = t(1:length(recovered));

// Normalize recovered signal

recovered = recovered / max(abs(recovered));

// Plotting

subplot(4,1,1);

plot(t,m);

xlabel("Time (s)");

ylabel("Amplitude");

title("Message Signal");

subplot(4,1,2);

plot(t,c);

xlabel("Time (s)");

ylabel("Amplitude");

title("Carrier Signal");

subplot(4,1,3);

plot(t,dsb_sc);

xlabel("Time (s)");

ylabel("Amplitude");

title("DSB-SC Modulated Signal");

subplot(4,1,4);

plot(t_rec,recovered);

xlabel("Time (s)");

ylabel("Amplitude");

title("Demodulated / Recovered Signal");
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
