The magical file to quickly get a solution to a problem encountered before without searching the Internet.

# Trigonometry

## Cosine $\rightarrow$ Sine Conversion

$$\cos{(\theta - 90)} = \sin{(\theta)}$$
$$\sin{(\theta + 90) = \cos{(\theta})}$$

# RLC Circuit Analysis

## Impedance of Series Circuit : 

$$Z^2 = R^2 + (X_L - X_C)^2$$

Impedance of Inductor : $X_L = 2\pi fL$

Impedance of Capacitor : $X_C = \frac{1}{2\pi fC}$


## Leading/Lagging Component

- **ELI** the **ICE** man 
- Voltage Leads Current in Inductor Circuit.
- Current Leads Voltage in Capacitor Circuit.

## Reactive Power 

$$Q = VI\sin(\theta)$$

- Resistive Load    : $Q_L = I^2X_L$
- Capacitive Load   : $Q_C = I^2X_C$

## Phase Relationships

$$S = P + jQ = VI\cos(\theta) + jVI\sin(\theta) = VI\angle\theta$$

- Real Power : $P = VI_{in}$
- Reactive Power : $Q = VI_{out}$
- Apparent Power : $S = \sqrt{Q^2 - P^2}$

# Signal Analysis

## Aliasing

Example :

$$x_a(t) = 3 \cos(600\pi t) + 2 \cos(1800\pi t)$$

- Sampling Frequency : 1000 Hz
- Aliasing : $\text{Sampling frequency} \leq 2 F$

Frequencies in Resulting Discrete-time signal :

- $f_1 = \frac{F_1}{F_s} = \frac{300}{1000} = 0.3 \text{ cycles/sample}$
- $f_2 = \frac{F_2}{F_s} = \frac{900}{1000} = 0.9 \text{ cycles/sample}$
- $f_2$ appearing as $f^\text{alias}_2 = 0.9 - 1 = - 0.1 \text{ cycles/sample}$
- $f_2 = \frac{F_2}{F_s} = \frac{900}{1000} = 0.9 \text{ cycles/sample}$

## Power and Energy of Signal

### Energy

$$E = \sum_{n = - \infty}^{\infty} |x(n)|^2$$

### Power

$$P = \lim_{N \rightarrow \infty} \frac{1}{2N + 1} \sum_{n=-N}^{N} |x(n)|^2$$

For $x(n) = A \cos(2\pi fn + \phi)$ :

$$P = \frac{A^2}{2}$$

## Impulse Response

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

## Steady-state response
Example : 

$$\begin{aligned}
x(n) & = 2 \cos(0.1\pi n)u(n)\\
H(z) & = \frac{1 - 0.5z^{-1}}{1 - \dfrac{1}{12} z^{-1} + \dfrac{1}{12} z^{-2}}\\
\end{aligned}$$

1. Frequency Response. $H(jw) = H(z)|_{z \equiv e^{jw}} = 1.0332 \times e^{0.358j}$
2. Fundamental Frequency. $w_0 = 0.1\pi$
3. Substitute Fundamental Frequency into Frequency Response.
4. Steady-state Response. $y(n) = 2 \times 1.0332 \times \cos(0.1\pi n + 0.358) u(n)$

## Zero-state Step Response

The step response is the system's output when the input is $u(n)$.

## Zero-input Response

- Poles of the system.

$$y_{zi} = [A(p_1)^n + B(p_2)^n]u(n)$$

## Stability of a System

Determine if the poles of the system are within the unit circle.

## Initials and Final Values of Causal Signal
- Signal is causal

### Initial Value

$$\lim_{z \rightarrow \infty} z^{-1} = 0$$

### Final Value

$$\lim_{z \rightarrow 1} z^{-1} = 1$$

## Statistical Calculations

### Mean

$$\mu = E[X] = \int_{-\infty}^{\infty} xp(x) dx$$

### Mean Square

$$\mu = E[X^2] = \int_{-\infty}^{\infty} x^2p(x) dx$$

### Variance

$$Var[X] = E[X^2] - \mu^2$$

### Standard Deviation

$$\sigma = \sqrt{Var[X]}$$

## Quantisation Noise

$$\Delta = \frac{x_{max}-x_{min}}{L}$$

### Variance of Quantisation Noise
Signal Power is also equal to Quantisation Noise variance.

$$P_{signal} = \delta^2 = \Delta/12$$

### Signal to Quantisation-Noise Ratio

$$SQNR = \frac{P_{signal}}{P_{noise}} = L^2$$

## Autocorrelation Sequence

$$r_{xx}(l) = \sum_{n=-\infty}^{\infty} x(n)x(n-l)$$

With number sequences :

``` c
x(n) = {1, 2, 1, 1}
```

- Do multiplication with

``` c
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

## Communication System

Information Source -> Input Transducer -> Transmitter -> Channel
-> Receiver -> Output Transducer -> Sink

Source Encoder -> Channel Encoder -> Modulator

Demodulator -> Channel Decoder -> Source Decoder

## Instantaneous Frequency

Example :

$$x(t) = 2\cos(2\pi 10t + 10 \pi t^2)$$

Instantaneous Frequency :

$$f(t) = \frac{1}{2\pi} \frac{d(2\pi 10t + 10 \pi t^2)}{dt} = 10 + 10t$$

### VCO

Instantaneous Frequency :

$$f(t) = f_c + k_f m(t)$$

## AM Modulation

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

## FM Modulation

### FM Modulation Index

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

### Narrowband FM

Magnitude Spectrum :

$$e(t) \approx A_c \cos(w_ct)- A_c \mu_f \sin(w_m t)\sin(w_c t)$$

$$e(t) \approx A_c \cos(w_ct)- \frac{A_c \mu_f}{2} \cos(w_c - w_m)t + \frac{A_c \mu_f}{2} \cos(w_c + w_m)t$$

Example :

Draw a double-sided magnitude spectrum for the Narrowband FM signal.

$$e(t) = 10 \cos[2\pi 10^7t+ 0.2\cos(2\pi 10^4t)]$$

- $\mu_f = 0.2$

$$e(t) = A_c \cos(2\pi 10^7t+)- A_c \mu_f \cos(2\pi 10^4t)\sin(2\pi 10^7t+)$$

- Carrier Signal has amplitude of 5 and two side-bands which are message signals with amplitude of 0.5

### Wideband FM

$$\begin{aligned}
e(t) & = A_c J_n (\mu_f) \cos(w_ct)\\
& + \sum_{n \text{even}}^{\infty} A_c J_n (\mu_f)[\cos(w_c + nw_m)t + \cos(w_c - nw_m)t]\\
& + \sum_{n \text{odd}}^{\infty} A_c J_n (\mu_f)[\cos(w_c + nw_m)t - \cos(w_c - nw_m)t]\\
\end{aligned}$$

- FM spectrum has carrier frequency line and **infinite** number of side-band lines at $f_c \pm nf_m$.
- Lines equally spaced by $f_m$.
- Odd-order lower side-band lines reversed in phase.
- $J_n(\mu_f)$ obtained from the Bessel Function Values table.

### Bessel Function Values Table

![Bessel Function Values Table](images/BesselFunction.png){ width=80% }

### Modulated Signal

Example :

Carrier given by $c(t) = 10 \cos (2\pi f_ct)$. Message Signal $\cos(20\pi t)$. 
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

## Bandwidth of FM Signals

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

## Information Measure

### Entropy Example

``` matlab
Source = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

P(1)=P(6)=P(7)=P(10)=1/16

P(2)=P(3)=P(4)=P(5)=P(8)=P(9)=2/16
```

$\begin{aligned}
Entropy &= 4\times -\frac{1}{16}\log_2{\frac{1}{16}} + 6 \times -\frac{2}{16}\log_2{\frac{2}{16}}\\
&= 3.25 bits
\end{aligned}$

### Source Coding Example

``` matlab
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

## Source Rate

$$R = \frac{H}{T}$$

- H, Entropy
- T, Time

## Noiseless Channel Capacity

$$C=2B\log_2{M}$$

$$C=B\log_2{(1+\frac{S}{N})}$$

- B, Bandwidth
- M, Level Signalling
- C, Channel Capacity

## Signal-to-Noise Ratio (SNR)

$$SNR=\frac{P_x}{P_n}$$

$$SNR_{db} = 10\log_{10}{SNR}$$

## Quantisation

### Uniform Quantisation

\
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

### $\mu$-Law Warping/Unwarping

\
Sample Compressing (Warping) + Uniform Quantisation + Sample Expanding (Unwarping)

$\mu$-Law Warping :
$$F(x)=x_{max}\frac{ln{(1+\mu[\frac{|x|}{x_{max}}])}}{ln(1+\mu)} \cdot sgn(x)$$

$\mu$-Law Unwarping :

$$\hat{x}=F^{-1}(F(x))=\frac{x_{max}}{\mu}[(1+\mu)^{\frac{|F(x)|}{x_{max}}} -1] \cdot sgn(F(x))$$

## Encoding

| Type of Encoding        | Characteristics                                                                |
|-------------------------|--------------------------------------------------------------------------------|
| Unipolar                | Only 1s and 0s                                                                 |
| NRZ-L                   | Positive voltage mean 0 <br> Negative voltage mean 1                           |
| NRZ-I                   | Transition when next bit is 1                                                 |
| RZ                      | Positive, Negative and 0<br> Change to 0 and Positive for 1 and Negative for 0 |
| Manchester              | Low -> High represents 1<br>  High -> Low represents 0                         |
| Differential Manchester | Transition at beginning means 0<br> No transition means 1                      |

## Raised Cosine Pulse Shaping

Bandwidth :
$$B_{RC}=\frac{1-\alpha}{2T}$$

Efficiency :

$$E_{RC}=\frac{2}{1-\alpha}$$

## Pulse Shaping

| Type of Pulse Shaping | Characteristics                                                        |
|-----------------------|------------------------------------------------------------------------|
| Nyquist               | Problems :<br>- Time duration long<br>- Ideal Synchronisation Required |
| Raised Cosine         | Reduce Intersymbol Interference (ISI)                                  |

## Matched Filtering

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

## Equalisation

- Equalising Filter to minimise ISI
- Two types :
    - Zero Forcing Equaliser
    - MMSE Equaliser

## Digital Modulation

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

## Discrete Time Fourier Transform (DTFT)

DTFT :

$$X(jw) = \sum_{n=-\infty}^{\infty} x[n]e^{-jwn}$$

IDTFT :

$$x[n] = \frac{1}{2\pi} \int_{w=-\pi}^{\pi} X(jw)e^{jwn} dw$$

## Discrete Fourier Transform (DFT)

DFT :

$$X[k] = \sum_{n=0}^{N-1} x[n]e^{-j\frac{2\pi k}{N}}n$$

IDFT:

$$X[n] = \frac{1}{N} \sum_{k=0}^{N-1} X[k] e^{j\frac{2\pi k}{N}}$$

## Geometric Series

$$\sum_{n=0}^{N-1} a^n = \frac{1-a^{N-1+1}}{1-a}$$

## Circular Convolution

Time domain Method :

$$y(m) \equiv \sum_{n=0}^{N-1} x_1(n) x_2((m-n)_N)$$

DFT and IDFT Method :

1. Find DFT's of the input sequences
2. Product of the two DFT's
3. Inverse DFT

Example :

```matlab
x_1(n) = {1,3,5,7}
x_2(n) = {2,4,6,8}
```

$$X_1(k) = 1 + 3 W_{4}^{k} + 5 W_{4}^{2k} + 7 W_{4}^{3k}$$
$$X_2(k) = 2 + 4 W_{4}^{k} + 6 W_{4}^{2k} + 8 W_{4}^{3k}$$

Product of two DFT , $Y(k) = X_1(k) X_2(k) = 84 + 92 W_{4}^{k} + 84 W_{4}^{2k} + 60 W_{4}^{3k}$

Inverse DFT , $y(n)={84,92,84,60}$

## Direct Form Realisation

Transfer Function :

$$H(z) = \frac{Y(z)}{X(z)}$$

- Top portion is non-recursive
- Bottom portion is recursive

Cascade Form :

$$H(z) = CH_1(z)H_2(z)$$

- Splitting the two fractions into different direct form II
- Multiply by the constant at the end

Parallel Form :

- Partial Fraction Decomposition to get different terms
- Each term is a sub-system by itself
- Sums after computation within each sub-system

# AVR Programming

## Common Items at8515

### Alternate Functions of Port D
| Port Pin | Alternate Function                                  |
|----------|-----------------------------------------------------|
| PD7      | RD (Read Strobe to External Memory)                 |
| PD6      | WR (Write Strobe to External Memory)                |
| PD5      | OC1A (Timer/Counter1 Output Compare A Match Output) |
| PD4      | XCK (USART External Clock Input/Output)             |
| PD3      | INT1 (External Interrupt 1 Input)                   |
| PD2      | INT0 (External Interrupt 0 Input)                   |
| PD1      | TXD (USART Output Pin)                              |
| PD0      | RXD (USART Input Pin)                               |

### Pointer Register Locations

| Pointer Register     | HEX | DEC | BIN   |
|----------------------|-----|-----|-------|
| X-Register Low Byte  | 1A  | 26  | 11010 |
| X-Register High Byte | 1B  | 27  | 11011 |
| Y-Register Low Byte  | 1C  | 28  | 11100 |
| Y-Register High Byte | 1D  | 29  | 11101 |
| Z-Register Low Byte  | 1E  | 30  | 11110 |
| Z-Register High Byte | 1F  | 31  | 11111 |

### AVR Addressing Mode

| Addressing Mode                              | Example        |
|----------------------------------------------|----------------|
| I/O Direct Addressing                        | IN r8, SPL     |
| Immediate Addressing                         | ANDI r16, 0x0D |
| Data Direct Addressing                       | STS 0x00AA, r2 |
| Data Indirect Addressing (no +-)             | ST Y, r13      |
| Data Indirect Addressing with Post-Increment | ST Y+, r28     |
| Data Indirect Addressing with Pre-Decrement  | LD r15, -X     |
| Data Indirect Addressing with Displacement   | LDD Z+1, r21   |

### Interrupt Sense Control

```asm
    ; *** set up & enable interrupts ***
    ; ISC11 = 0 ISC10 = 1
    ldi temp, (1<<ISC11) | (1<<ISC10) | (0<<ISC01) | (1<<ISC00)
    out MCUCR,temp

    ldi temp, (1<<INT1) | (1<<INT0)
    out GICR, temp

    sei
```

| ISC11 | ISC10 | Description          |
|-------|-------|----------------------|
| 0     | 0     | Low INT1 Trigger     |
| 0     | 1     | Any INT1 Trigger     |
| 1     | 0     | Falling edge Trigger |
| 1     | 1     | Rising edge Trigger  |

### Status Register (SREG)

- Bit 7 – I: Global Interrupt Enable
- Bit 6 – T: Bit Copy Storage
- Bit 5 – H: Half Carry Flag
- Bit 4 – S: Sign Bit, S = N $\bigoplus$ V
- Bit 3 – V: Two’s Complement Overflow Flag
- Bit 2 – N: Negative Flag
- Bit 1 – Z: Zero Flag
- Bit 0 – C: Carry Flag

## Common Items atmega16

I/O Port for TXD and RXD
- TXD = PD1
- RXD = PD0

Register to set baud rate
- UBRRH, UBRRL

Asynchronous transmission
- UMSEL (Register UCSRC)

Number of stop bits
- USBS (Register UCSRC)
    - 0 -> 1 Stop bit
    - 1 -> 2 stop bit

Parity bit options
- UPM1, UPM0 (Register UCSRC)
    - 00 -> None
    - 10 -> Even
    - 11 -> Odd

Double Transmission Speed
- U2X = 1 (Register UCSRA)
- Baud Rate = $\text{Clock}/[8 \times (UBRR + 1)$

Character Size 5, 6, 8, 9
- UCSZ2 (UCSRB)
- UCSZ1, UCSZ0 (UCSRC)

Initialise serial port 
1. Set USART for asynchronous mode (UCSRA, UCSRC)
2. Set USART communication parameters (UCSRA, UCSRC)
3. Set baud rate (UBRRH, UBRRL)
4. Enable transmitter and receiver (UCSRB)

Synchronous VS Asynchronous Serial Transmission
- Synchronous
    - Clocks of sender and receiver are synchronised
    - Block of characters enclosed by synchronising bytes sent at a time
    - Faster transfer and less overhead
    - SPI/ BISYNC
- Asynchronous
    - Clock of sender and receiver not synchronised
    - One character sent at a time enclosed by start bit, stop bit & parity
    - Slow for long messages, suitable for interactive messages

Timing in asynchronous serial transmission
- Each character requires 11 bits to send : 8 data + 1 start + 1 stop + 1 parity
- Receiver reads the 11th bit to find the end of the transmission
    - If not detected, a framing error will occur
- Clock period $T_{tx}$ 
    - $T_{tx} = 1/\text{baud rate}$

Example:

A file of 10000 bytes sent over a line at 19600bps
1. Calculate overhead in bits and seconds for asynchronous mode.
    - 1 start bit, 1 stop bit, 8 data bits and no parity bit
2. Calculate the overhead in bits and seconds for synchronous mode.
    - 1000 characters/frame and overhead of 48bits/frame

1. 1 start and 1 stop bit = 2 bits of overhead per character.
    - 20000 bits sent
    - overhead = 20000/19600 = 1.02s
2. 10 frames to transmit file
    - overhead bits 48bits/frame
    - overhead time = 48*10/19600 = 0.0245s

## Timers in ATmega16
- Bit width of Timer 0, Timer 1 and Timer 2
    - Timer 0 -> 8 bits
    - Timer 1 -> 16 bits
    - Timer 2 -> 8 bits
- TCNT registers store current counter value
- Select clock source for Timer 1
    - TCCR1B
        - CS12
        - CS11
        - CS10
- Prescaler only applied to internal clock source
- Enable Timer 1 interrupts
    - TIMSK
- Timer 1 overflow if uses the default internal clock of 1MHz and prescaler factor of 1024
    - $1 \mu s \times 1024 \times 2^16 = 67s$
- Register select the type of events trigger Timer 1 Input Capture Interrupt
    - TCCR1B (ICES1)
- Stores automatically the timer value when Timer 1 Input Capture interrupt occurs
    - ICR1
- I/O Port for Input Capture Pin
    - Port D pin 6 (D.6)

### Timer 1 Input Capture Interrupt
- Timer 1 can either detect rising edge or falling edge

Possible solution
- Trigger External Internet INT1 on rising edge
    - When INT1 occurs reset Timer 1
- Trigger Timer 1 Input Capture Interrupt on falling edge
    - When TIMER1_CAP occurs, read ICR1
- Feed Rectangular signal to INT1 (D.3)

# Data Communications

N(R) = ACK

