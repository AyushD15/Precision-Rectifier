# Why Precision Rectifiers?

In normal rectifiers using diodes, the forward voltage drop (~0.7 V for silicon, ~0.3 V for Schottky) causes distortion when working with very small input signals (say, in mV range).
👉 This makes normal rectifiers unsuitable for low-signal applications like audio processing, instrumentation, and AC voltmeters.

A precision rectifier overcomes this by using an op-amp + diode combination. The op-amp ensures that even tiny voltages get rectified correctly, eliminating the threshold issue.

## 1. Half-Wave Precision Rectifier
![alt text](https://github.com/AyushD15/Precision-Rectifier/blob/main/Precision-Half-Wave-Rectifier.jpg)
This circuit passes only one half of the input signal (positive or negative depending on diode orientation).

### Circuit Functioning
> 𝑉𝑖𝑛 → through 𝑅1 → inverting input of op-amp (−).
> Non-inverting input (+) grounded (so virtual ground concept applies when feedback works).
> Two diodes:
    > D1 at op-amp output → series → Vout.
    > D2 from op-amp output back to inverting input node through 𝑅2.
> R2 provides negative feedback only when D2 conducts.

This arrangement solves the op-amp saturation problem of the simple superdiode.
