The magical file to quickly get a solution to a problem encountered before without searching the Internet.

## Table of Content

  * [Aliasing](#aliasing)
  * [Power and Energy of Signal](#power-and-energy-of-signal)
    * [Energy](#energy)
    * [Power](#power)
  * [Impulse Response](#impulse-response)
  * [Steady-state response](#steady-state-response)
  * [Zero-state Step Response](#zero-state-step-response)
  * [Zero-input Response](#zero-input-response)
  * [Stability of a System](#stability-of-a-system)
  * [Initials and Final Values of Causal Signal](#initials-and-final-values-of-causal-signal)
    * [Initial Value](#initial-value)
    * [Final Value](#final-value)
  * [Statistical Calculations](#statistical-calculations)
    * [Mean](#mean)
    * [Mean Square](#mean-square)
    * [Variance](#variance)
    * [Standard Deviation](#standard-deviation)
  * [Quantisation Noise](#quantisation-noise)
    * [Variance of Quantisation Noise](#variance-of-quantisation-noise)
    * [Signal to Quantisation-Noise Ratio](#signal-to-quantisation-noise-ratio)
  * [Autocorrelation Sequence](#autocorrelation-sequence)
  * [Communication System](#communication-system)
  * [Instantaneous Frequency](#instantaneous-frequency)
    * [VCO](#vco)
  * [AM Modulation](#am-modulation)
  * [FM Modulation](#fm-modulation)
    * [FM Modulation Index](#fm-modulation-index)
    * [Narrowband FM](#narrowband-fm)
    * [Wideband FM](#wideband-fm)
    * [Bessel Function Values Table](#bessel-function-values-table)
    * [Modulated Signal](#modulated-signal)
  * [Bandwidth of FM Signals](#bandwidth-of-fm-signals)
  * [Information Measure](#information-measure)
    * [Entropy Example](#entropy-example)
    * [Source Coding Example](#source-coding-example)
  * [Source Rate](#source-rate)
  * [Noiseless Channel Capacity](#noiseless-channel-capacity)
  * [Signal-to-Noise Ratio (SNR)](#signal-to-noise-ratio-(snr))
  * [Quantisation](#quantisation)
    * [Uniform Quantisation](#uniform-quantisation)
    * [$\mu$-Law Warping/Unwarping](#$\mu$-law-warping/unwarping)
  * [Encoding](#encoding)
  * [Raised Cosine Pulse Shaping](#raised-cosine-pulse-shaping)
  * [Pulse Shaping](#pulse-shaping)
  * [Matched Filtering](#matched-filtering)
  * [Equalisation](#equalisation)
  * [Digital Modulation](#digital-modulation)

### Aliasing

Example :

$$x_a(t) = 3 \cos(600\pi t) + 2 \cos(1800\pi t)$$

- Sampling Frequency : 1000 Hz
- Aliasing : $\text{Sampling frequency} \leq 2 F$

Frequencies in Resulting Discrete-time signal :
- $f_1 = \frac{F_1}{F_s} = \frac{300}{1000} = 0.3 \text{ cycles/sample}$
- $f_2 = \frac{F_2}{F_s} = \frac{900}{1000} = 0.9 \text{ cycles/sample}$

$f_2$ appearing as $f^\text{alias}_2 = 0.9 - 1 = - 0.1 \text{ cycles/sample}$

- $f_2 = \frac{F_2}{F_s} = \frac{900}{1000} = 0.9 \text{ cycles/sample}$

### Power and Energy of Signal

#### Energy

$$E = \sum_{n = - \infty}^{\infty} |x(n)|^2$$

#### Power

$$P = \lim_{N \rightarrow \infty} \frac{1}{2N + 1} \sum_{n=-N}^{N} |x(n)|^2$$

For $x(n) = A \cos(2\pi fn + \phi)$ :

$$P = \frac{A^2}{2}$$

### Impulse Response

1. System Equation
2. Impulse Response
3. Characteristic Equation from Poles
4. General Form
5. Impulse Response from General Form

Example :

$$y(n) = 0.25y(n-1) + \frac{1}{8}y(n-2) + x(n) - x(n-1)$$


$\begin{aligned}
\text{ Impulse Response : } & h(n) = 0.25h(n-1) + \frac{1}{8}h(n-2) + \delta(n) - \delta(n-1)\\
\text{ Characteristic Equation : } & \lambda^2 - 0.25\lambda - 0.125 = 0 \quad \lambda_1 = 0.5, \lambda_2 = -0.25\\ 
\text{ General Form : } & h(n) = c_1(0.5)^n + c_2(-0.25)^n \text{ for n } \geq 1
\end{aligned}$

From Impulse Response :

$$h(0) = 1, h(1) = -0.75, h(2) = -0.0625$$

From General Form :

$\begin{aligned}
n & = 1 : 0.5c_1 -0.25c_2 = - 0.75\\
n & = 2 : 0.25c_1 - 0.0625c_2 = - 0.0625\\
\end{aligned}$

$c_1 = - \dfrac{2}{3}, c_2 = \dfrac{5}{3}$

Impulse Response from General Form :

$$h(n) = (-2/3)(0.5)^n + (5/3)(-0.25)^n \text{ for } n \geq 0$$

### Steady-state response
Example : 

$$\begin{aligned}
x(n) & = 2 \cos(0.1\pi n)u(n)\\
H(z) & = \frac{1 - 0.5z^{-1}}{1 - \dfrac{1}{12} z^{-1} + \dfrac{1}{12} z^{-2}}\\
\end{aligned}$$

1. Frequency Response. $H(jw) = H(z)|_{z \equiv e^{jw}} = 1.0332 \times e^{0.358j}$
2. Fundamental Frequency. $w_0 = 0.1\pi$
3. Substitute Fundamental Frequency into Frequency Response.
4. Steady-state Response. $y(n) = 2 \times 1.0332 \times \cos(0.1\pi n + 0.358) u(n)$

### Zero-state Step Response

The step response is the system's output when the input is $u(n)$.

### Zero-input Response

- Poles of the system.

$$y_{zi} = [A(p_1)^n + B(p_2)^n]u(n)$$

### Stability of a System

Determine if the poles of the system are within the unit circle.

### Initials and Final Values of Causal Signal
- Signal is causal

#### Initial Value

$$\lim_{z \rightarrow \infty} z^{-1} = 0$$

#### Final Value

$$\lim_{z \rightarrow 1} z^{-1} = 1$$

### Statistical Calculations

#### Mean

$$\mu = E[X] = \int_{-\infty}^{\infty} xp(x) dx$$

#### Mean Square

$$\mu = E[X^2] = \int_{-\infty}^{\infty} x^2p(x) dx$$

#### Variance

$$Var[X] = E[X^2] - \mu^2$$

#### Standard Deviation

$$\sigma = \sqrt{Var[X]}$$

### Quantisation Noise

$$\Delta = \frac{x_{max}-x_{min}}{L}$$

#### Variance of Quantisation Noise
Signal Power is also equal to Quantisation Noise variance.

$$P_{signal} = \delta^2 = \Delta/12$$

#### Signal to Quantisation-Noise Ratio

$$SQNR = \frac{P_{signal}}{P_{noise}} = L^2$$

### Autocorrelation Sequence

$$r_{xx}(l) = \sum_{n=-\infty}^{\infty} x(n)x(n-l)$$

With number sequences :
```
x(n) = {1, 2, 1, 1}
```

- Do multiplication with

```
      1 2 1 1
      1 1 2 1 \\ Inverted x(n)
-------------
      1 2 1 1
    2 4 2 2 0
  1 2 1 1 0 0
1 2 1 1 0 0 0
-------------
1 3 5 7 5 3 1
```

### Communication System

Information Source -> Input Transducer -> Transmitter -> Channel
-> Receiver -> Output Transducer -> Sink

Source Encoder -> Channel Encoder -> Modulator

Demodulator -> Channel Decoder -> Source Decoder

### Instantaneous Frequency

Example :

$$x(t) = 2\cos(2\pi 10t + 10 \pi t^2)$$

Instantaneous Frequency :

$$f(t) = \frac{1}{2\pi} \frac{d(2\pi 10t + 10 \pi t^2)}{dt} = 10 + 10t$$

#### VCO

Instantaneous Frequency :

$$f(t) = f_c + k_f m(t)$$

### AM Modulation

Amplitude of AM Signal :

$$\begin{aligned}
A_{max} &= A_C(1+\mu)\\
A_{min} &= A_C(1-\mu)\\
A_m &= A_C \times \mu\\
\end{aligned}$$

Example :

$$x_c(t) = A_c[1 + \mu x(t)] \cos(w_ct)$$

Assuming that $\mu < 1$.

- Transmitted Power = $P_t = \langle x_c^2(t) \rangle$
- Power in Message Signal = $P_x = \langle x^2(t) \rangle$

Find an expression for transmitted power in terms of message power and modulation index.

Substitute expression for transmitted power :

$$P_t = \frac{1}{2} A_c^2 \langle 1 + 2\mu x(t) + \mu^2x^2(t) \rangle + \frac{1}{2} A_c^2 \langle [1+\mu x(t)]^2 \cos(2w_ct)$$

- Time average of a constant is the same.
- Twice the carrier frequency component was removed
- Message Signal has no DC Component $\langle x(t)\rangle = 0$

$$P_t = \frac{1}{2} A_c^2(1+ \mu^2P_x) = \frac{1}{2} A_c^2 + \frac{1}{2}A_c^2 \mu^2 P_x$$

- First term is unmodulated carrier power $\mu = 0$
- Second term is power in carrier plus the signal
- Significant percentage of power resides in the carrier and conveys no information.

### FM Modulation

#### FM Modulation Index

$$\mu_f = \frac{A_mk_f}{f_m}$$

- $A_mk_f \leftarrow \text{ Maximum Frequency Deviation , } f_{max}$
- Narrowband FM, $\mu_f << 1$

Example : 

VCO has sensitivity constant of $3 kHz/V$ and free running frequency of $1 MHz$. Input to VCO is tone signal with peak amplitude equal to $2 V$ and frequency $4 kHz$. Output signal is FM. Calculate modulation index of the output FM Signal. 

$$\begin{aligned}
f_c &= 1\times 10^6 \quad k_f = 3\times 10^3 \quad f(t) =f_c +k_fm(t)\\
m(t) &= A_m\cos(2\pi f_m t) = 2\cos(2\pi \times 4000t)\\
f_{max} &=k_f max\{|m(t)|\} = 3\times 10^3 \times 2 = 6 \times 10^3 Hz\\
\mu_f &= \frac{6kHz}{4KHz} = 1.5
\end{aligned}$$

#### Narrowband FM

Magnitude Spectrum :

$$e(t) \approx A_c \cos(w_ct)- A_c \mu_f \sin(w_m t)\sin(w_c t)$$

$$e(t) \approx A_c \cos(w_ct)- \frac{A_c \mu_f}{2} \cos(w_c - w_m)t + \frac{A_c \mu_f}{2} \cos(w_c + w_m)t$$

Example :

Draw a double-sided magnitude spectrum for the Narrowband FM signal.

$$e(t) = 10 \cos[2\pi 10^7t+ 0.2\cos(2\pi 10^4t)]$$

- $\mu_f = 0.2$

$$e(t) = A_c \cos(2\pi 10^7t+)- A_c \mu_f \cos(2\pi 10^4t)\sin(2\pi 10^7t+)$$

- Carrier Signal has amplitude of 5 and two side-bands which are message signals with amplitude of 0.5

#### Wideband FM

$$\begin{aligned}
e(t) & = A_c J_n (\mu_f) \cos(w_ct)\\
& + \sum_{n \text{even}}^{\infty} A_c J_n (\mu_f)[\cos(w_c + nw_m)t + \cos(w_c - nw_m)t]\\
& + \sum_{n \text{odd}}^{\infty} A_c J_n (\mu_f)[\cos(w_c + nw_m)t - \cos(w_c - nw_m)t]\\
\end{aligned}$$

- FM spectrum has carrier frequency line and **infinite** number of side-band lines at $f_c \pm nf_m$.
- Lines equally spaced by $f_m$.
- Odd-order lower side-band lines reversed in phase.
- $J_n(\mu_f)$ obtained from the Bessel Function Values table.



#### Modulated Signal

Example :

Carrier given by $c(t) = 10 \cos (2pif_ct)$. Message Signal $\cos(20\pi t)$. 
The message is used to frequency modulate the carrier with $k_f=50$. 
Find expression for modulated signal, determine how many harmonics selected to contain $99\%$ of modulated power.

From message signal :

$$f_m = 10Hz$$

Modulated Signal : 

$$\begin{aligned}
e(t) & = A\cos(2\pi f_c t + 2\pi k_f \int_{-\infty}^{t} \cos(20\pi \tau) d\tau\\
& = 10 \cos(2\pi f_c t + \frac{100\pi}{20\pi} \sin(20\pi t))\\
& = 10 \cos(2\pi f_c t + 5 \sin(20\pi t)\\
\end{aligned}$$

Modulation index :

$$\mu_f = 5$$

FM Modulated Signal :

$$e(t)= 10 \cos(2\pi f_c t + 5 \sin(20\pi t)$$

Total Power :

$$P = \frac{A^2}{2} = 100/2 = 50$$

Spectral lines are at $f_c \pm 10n$
- How many of the lines contain 99% of the total power.

General FM Signal Spectrum :

$$\begin{aligned}
e(t) & = A_c J_n (\mu_f) \cos(w_ct)\\
& + \sum_{n \text{even}}^{\infty} A_c J_n (\mu_f)[\cos(w_c + nw_m)t + \cos(w_c - nw_m)t]\\
& + \sum_{n \text{odd}}^{\infty} A_c J_n (\mu_f)[\cos(w_c + nw_m)t - \cos(w_c - nw_m)t]\\
\end{aligned}$$

- $A_c = 10$ and $\mu_f = 5$
- Power in carrier line $\frac{A_cJ_0(\mu_f))^2}{2} = \frac{100J_0^2(5)}{2}$

Value of $k$ such that at least 99% of power is covered :

$$\sum_{n=-k}^{k} \frac{100J_0^2(5)}{2} \geq 0.99 P$$

- $k = 6$
- Significant spectral lines at $f_c \pm 10k \text{ , } k = 1, ... ,6$
- Effective bandwidth = $120 Hz$ ($60Hz$ on both sides of carrier)

### Bandwidth of FM Signals

- Bandwidth of FM signal depends on $f_m$ and $\mu_f$

**Carson's Rule** : 98% of total power is contained in bandwidth.

$$B_c = 2(\mu_f + 1)W$$

- Modulation Index, $\mu_f$ 
- Bandwidth of message signal, $W$

Example :

$$m(t) = 10 \text{sinc }(10^4 t)$$

Determine transition bandwidth of FM modulated signal with $k_f = 4000$.

$$m(t) = \frac{10}{10^4t}\sin(10^4 \pi t)$$

- Sinc function can be converted to sine function.
- Bandwidth , $W = 5000Hz$

$$f_{max} = k_f max\{|m(t)|\} = 4000 \times 10 = 40 kHz$$

$$\mu_f = \frac{f_{max}}{W} = \frac{40k}{5k} = 8$$

$$B_c = 2(8 + 1)5k = 90kHz$$

### Information Measure

#### Entropy Example

```matlab
Source = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

P(1)=P(6)=P(7)=P(10)=1/16

P(2)=P(3)=P(4)=P(5)=P(8)=P(9)=2/16
```
$\begin{aligned}
Entropy &= 4\times -\frac{1}{16}\log_2{\frac{1}{16}} + 6 \times -\frac{2}{16}\log_2{\frac{2}{16}}\\
&= 3.25 bits
\end{aligned}$

#### Source Coding Example

```matlab
% Source has alphabet = {A B C D} 

P(A)=0.25,  P(B)=0.5,  P(C)=0.125,  P(D)= 0.125
```

Encoder 1 :
- Encode 4 elements into 2 bits

| Element | Bit |
|---------|-----|
| A       | 00  |
| B       | 01  |
| C       | 10  |
| D       | 11  |

Encoder 2 :
- Account Probabilities

| Element | Bit |
|---------|-----|
| A       | 10  |
| B       | 0   |
| C       | 110 |
| D       | 111 |

### Source Rate

$$R = \frac{H}{T}$$

- H, Entropy
- T, Time

### Noiseless Channel Capacity

$$C=2B\log_2{M}$$

$$C=B\log_2{(1+\frac{S}{N})}$$

- B, Bandwidth
- M, Level Signalling
- C, Channel Capacity

### Signal-to-Noise Ratio (SNR)

$$SNR=\frac{P_x}{P_n}$$

$$SNR_{db} = 10\log_{10}{SNR}$$

### Quantisation
#### Uniform Quantisation
Step Size :
$$\Delta=\frac{(x_{max}-x_{min})}{L}$$

- $L=2^n$, Number of discrete levels

$$Eq(l) =|x-q_l| \qquad q_l=x_{min} + \Delta/2 +l\times\Delta$$

Accuracy :
$$\text{Accuracy} = \frac{E}{D}$$

Maximum Quantisation Error :
$$E=\frac{\Delta}{2}$$

Bit Rate :
$$R=f_s \times n$$

#### $\mu$-Law Warping/Unwarping
Sample Compressing (Warping) + Uniform Quantisation + Sample Expanding (Unwarping)

$\mu$-Law Warping :
$$F(x)=x_{max}\frac{ln{(1+\mu[\frac{|x|}{x_{max}}])}}{ln(1+\mu)} \cdot sgn(x)$$

$\mu$-Law Unwarping :

$$\hat{x}=F^{-1}(F(x))=\frac{x_{max}}{\mu}[(1+\mu)^{\frac{|F(x)|}{x_{max}}} -1] \cdot sgn(F(x))$$

### Encoding

| Type of Encoding        | Characteristics                                                                |
|-------------------------|--------------------------------------------------------------------------------|
| Unipolar                | Only 1s and 0s                                                                 |
| NRZ-L                   | Positive voltage mean 0 <br> Negative voltage mean 1                           |
| NRZ-I                   | Transition when next bit is 1                                                 |
| RZ                      | Positive, Negative and 0<br> Change to 0 and Positive for 1 and Negative for 0 |
| Manchester              | Low -> High represents 1<br>  High -> Low represents 0                         |
| Differential Manchester | Transition at beginning means 0<br> No transition means 1                      |

### Raised Cosine Pulse Shaping

Bandwidth :
$$B_{RC}=\frac{1-\alpha}{2T}$$

Efficiency :

$$E_{RC}=\frac{2}{1-\alpha}$$

### Pulse Shaping

| Type of Pulse Shaping | Characteristics                                                        |
|-----------------------|------------------------------------------------------------------------|
| Nyquist               | Problems :<br>- Time duration long<br>- Ideal Synchronisation Required |
| Raised Cosine         | Reduce Intersymbol Interference (ISI)                                  |

### Matched Filtering

Matched Filter :
$$H(f)=K\frac{S^*(f)}{P_n(f)}e^{-j2\pi ft_0}$$

Impulse Response : 

$$h(t)=Cs(t_0-t)$$

- Known signal played backward and translated by $t_0$
- Autocorrelation function maximum when perfectly aligned

Power Spectral Density of White Noise :

$$P_n(f)=\frac{N_0}{2}$$

Probability of bit error :

$$P_e < \frac{e^{-E_b/N_0}}{2 \sqrt{\pi E_b/N_0}}$$

- $E_b$, Transmitted signal energy per bit
- $N_0$, Noise spectral density
- $\frac{E_b}{N_0}$ proportional to SNR

### Equalisation

- Equalising Filter to minimise ISI
- Two types :
    - Zero Forcing Equaliser
    - MMSE Equaliser

### Digital Modulation

$$a\cos (2\pi f_ct + \theta)$$

| Binary Shift Keyring    | Characteristics                                      |
|-------------------------|------------------------------------------------------|
| Frequency Shift Keyring | Carrier Frequency of signal changed to represent 1,0 |
| Amplitude Shift Keyring | Amplitude of signal changed to represent 1,0         |
| Phase Shift Keyring     | Phase of signal changed to represent 1,0             |

| M-ary Digital Modulation              | Characteristics                        |
|---------------------------------------|----------------------------------------|
| Quadrature PSK                        | Four phased used, represented by dibit |
| M-ary Quadrature Amplitude Modulation | Combines ASK and PSK                   |
| Differential PSK                      | Encode information in phase difference |

