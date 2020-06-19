[TOC]

The magical file to quickly get a solution to a problem encountered before without searching the internet.

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

### Inital and Final Values of Causal Signal
- Signal is causal

#### Inital Value

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
- Enocode 4 elements into 2 bits

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
| NRZ-I                   | Transistion when next bit is 1                                                 |
| RZ                      | Positive, Negative and 0<br> Change to 0 and Positive for 1 and Negative for 0 |
| Manchester              | Low -> High represents 1<br>  High -> Low represents 0                         |
| Differential Manchester | Transition at begining means 0<br> No transistion means 1                      |

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
- Autocorrelation function maximum when perfectly aliged

Power Spectral Density of White Noise :
$$P_n(f)=\frac{N_0}{2}$$

Probability of bit error :
$$P_e < \frac{e^{-E_b/N_0}}{2 \sqrt{\pi E_b/N_0}}$$
- $E_b$, Transmitted signal energy per bit
- $N_0$, Noise spectral density
- $\frac{E_b}{N_0}$ proportional to SNR

### Equalisation
- Equalising Filter to minmise ISI
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

