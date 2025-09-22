# 🔹Why Precision Rectifiers?

In normal rectifiers using diodes, the forward voltage drop (~0.7 V for silicon, ~0.3 V for Schottky) causes distortion when working with very small input signals (say, in mV range).
This makes normal rectifiers unsuitable for low-signal applications like audio processing, instrumentation, and AC voltmeters.

A precision rectifier overcomes this by using an op-amp + diode combination. The op-amp ensures that even tiny voltages get rectified correctly, eliminating the threshold issue.

## 1. Half-Wave Precision Rectifier
![alt text](https://github.com/AyushD15/Precision-Rectifier/blob/main/Precision-Half-Wave-Rectifier.jpg)
This circuit passes only one half of the input signal (positive or negative depending on diode orientation).

### 🔹Circuit Functioning
- 𝑉𝑖𝑛 → through 𝑅1 → inverting input of op-amp (−).
- Non-inverting input (+) grounded (so virtual ground concept applies when feedback works).
- Two diodes:
    - D1 at op-amp output → series → Vout.
    - D2 from op-amp output back to inverting input node through 𝑅2.
- R2 provides negative feedback only when D2 conducts.

This arrangement solves the op-amp saturation problem of the simple superdiode.

###  🔹 Case 1: Positive Half Cycle of 𝑉𝑖𝑛
- Suppose 𝑉𝑖𝑛 > 0
    - Current enters inverting input node via 𝑅1
    - The op-amp tries to keep the inverting input (−) at virtual ground (0 V).
    - To achieve this, op-amp output must swing negative.
- Now check diodes:
    - D2 (between op-amp output and inverting node) → forward biased, because op-amp output is negative while inverting input is near 0 V.
    - D1 (to output) → reverse biased, because op-amp output is negative and output node is near 0 V.
- only D2 conducts, giving a closed feedback loop.
    - The op-amp works as an inverting amplifier:
               VA​=−(R1/​R2)​​Vin​
      (where 𝑉𝐴 = op-amp output).  
    - Since D1 is OFF, no signal reaches Vout.
    - Hence, Vout​=0.
- During positive input cycle → Output is zero.

### 🔹 Case 2: Negative Half Cycle of 𝑉𝑖n
​- Suppose 𝑉𝑖𝑛 < 0
    - Current direction is opposite, so the op-amp must swing positive to maintain virtual ground at (−).
- Now check diodes:
    - D2 → reverse biased, because op-amp output is positive and inverting input node is near 0 V.
    - D1 → forward biased, because op-amp output is positive and output node is 0 V initially.
- So now D1 conducts, creating a feedback loop through load/output.
    - The op-amp + 𝑅1 , 𝑅2 work as an inverting amplifier:
               Vout​=−(R1/​R2)​​V
- Since 𝑉𝑖𝑛 is negative, − 𝑉𝑖𝑛 is positive.
    - Thus, Vout​=(R1/​R2​​)∣Vin​∣
- During negative input cycle → Output is a positive scaled replica.

### 🔹 Final Output Behavior
- For positive half cycle of input: 𝑉𝑜𝑢𝑡 = 0.
- For negative half cycle of input: 𝑉𝑜𝑢𝑡 = (𝑅2/𝑅1)∣𝑉𝑖𝑛|	​
- This is exactly a half-wave rectifier (but precision, since diode drop doesn’t matter due to op-amp action).

![alt text](https://github.com/AyushD15/Precision-Rectifier/blob/main/Half%20Wave%20Precision%20Rectifier/plot.png)

### 🔹 Key Advantages
- The op-amp never goes into deep saturation, so recovery is fast.
- Works for very small signals (mV range), because the diode drop is compensated by the op-amp.
- By choosing 𝑅2 = 𝑅1 , you get unity gain rectification:
               Vout​=∣Vin​∣(only negative half)

## 2. Full-Wave Precision Rectifier
![alt text](https://github.com/AyushD15/Precision-Rectifier/blob/main/Precision-Full-Wave-Rectifier.jpg)
This circuit allows both halves of the input waveform to appear at the output as rectified (absolute value function).

### 🔹Circuit Functioning
- Input signal: Vin
- First op-amp (A1): works as an inverting amplifier with diodes D1 and D2 steering current.
- Second op-amp (A2): works as a summing amplifier to combine signals from A1 and the input.
- Resistors: All chosen equal (R1 = R = R) for unity gain operation.

The diodes ensure that only one conduction path is active at a time, depending on the polarity of the input. This avoids op-amp saturation and allows rectification of very small signals.

###  🔹 Case 1: Positive Half Cycle of 𝑉𝑖𝑛
- Vin is positive.
- Op-amp A1 tries to invert the signal. To do this, its output goes negative.
- With A1 output negative:
     - D1 is reverse biased.
     - D2 is forward biased, so feedback is established through D2.
- Current flows through D2 and the resistor path into A2.
- At this point, A1’s output is inactive for the main output, and A2 simply inverts Vin through its summing arrangement.
- Final result: Vout is positive and equal to Vin (scaled by resistor ratios).

### 🔹 Case 2: Negative Half Cycle of 𝑉𝑖n
- Vin is negative.
- A1 tries to invert the signal. Its output goes positive.
- With A1 output positive:
     - D1 is forward biased.
     - D2 is reverse biased, so feedback is through D1.
- The positive output of A1 now drives A2 through the resistor network.
- A2 adds this with Vin, resulting in Vout = -Vin, which is again positive.
- Final result: Vout is positive and equal to the absolute value of Vin.

### 🔹 Final Output Behavior
- For Vin > 0: Vout = Vin (positive half is passed directly).
- For Vin < 0: Vout = -Vin (negative half is inverted to become positive).
- Therefore: Vout = |Vin| (the absolute value of the input).

![alt text](https://github.com/AyushD15/Precision-Rectifier/blob/main/Full%20Wave%20Precision%20Rectifier/plot.png)

### 🔹 Key Advantages
- Removes diode forward voltage drop issue (works even for millivolt inputs).
- Output is a clean full-wave rectified signal.
- Avoids op-amp saturation problems of simple rectifiers.
- Used in AC voltmeters, precision measurement, and signal conditioning.
