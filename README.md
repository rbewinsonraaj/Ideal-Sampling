**1.Experimental verification of Signal sampling using various types**
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
Google Colab

# Program
```
import numpy as np
import matplotlib.pyplot as plt
# Continuous signal parameters
fm = 5                      
fs = 50                     
t = np.linspace(0, 1, 1000) 
ts = np.arange(0, 1, 1/fs)  

# Original analog signal
x = np.sin(2 * np.pi * fm * t)#x=sin(2pifmt)

# Sampled values
xs = np.sin(2 * np.pi * fm * ts)

# Flat-top sampling generation
flat_top = np.zeros_like(t)

for i in range(len(ts)-1):
    idx = np.where((t >= ts[i]) & (t < ts[i+1]))
    flat_top[idx] = xs[i]

# Plotting
plt.figure(figsize=(12,8))

# Original signal
plt.subplot(4,1,1)
plt.plot(t, x)
plt.title("Original Analog Signal")
plt.grid()

# Ideal Sampling
plt.subplot(4,1,2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.grid()

# Natural Sampling (approximated)
plt.subplot(4,1,3)
plt.plot(t, x)
plt.stem(ts, xs, linefmt='r', markerfmt='ro', basefmt=" ")
plt.title("Natural Sampling")
plt.grid()

# Flat-top Sampling
plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.grid()

plt.tight_layout()
plt.show()
```
# Output Waveform

<img width="1189" height="790" alt="download" src="https://github.com/user-attachments/assets/c1fc1a30-5338-4dd2-8704-d0647901532a" />

# Results

Thus, the construction and reconstruction of Ideal, Natural, and Flat-top sampling were successfully implemented using Python, and the corresponding waveforms were obtained.

