# TECHNICAL SPECIFICATION: PHASED ARRAY AI ACCELERATOR ULTIMATE (PAAA-U)
# DOCUMENT VERSION: 1.0.0-RELEASE (SEPTEMBER 2026)
# LICENSE: MIT LICENSE
# AUTHOR: JUHO ARTTURI HEMMINKI
# ARCHITECTURE: CIRCULAR PHOTONIC INTERFERENCE MULTIPLEXING (CPIM)

================================================================================
MIT LICENSE
================================================================================
Copyright (c) 2026 Juho Artturi Hemminki

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
================================================================================

--------------------------------------------------------------------------------
1. ARCHITECTURAL PARADIGM SHIFT
--------------------------------------------------------------------------------
Modern silicon-based Deep Learning accelerators (GPUs, TPUs) are bound by the
von Neumann bottleneck and severe thermal limitations governed by Joule heating
($P = I^2R$). The Phased Array AI Accelerator Ultimate (PAAA-U) bypasses these
physical boundaries by implementing a completely transistorless computing fabric.

Instead of routing electrons through traditional logic gates, PAA-U utilizes
**Circular Photonic Interference Multiplexing (CPIM)**. Computation is achieved
by modulating the phase, amplitude, and spatial vectors of light waves inside an
isotropic, ring-shaped Optical Application-Specific Integrated Circuit (ASIC).

--------------------------------------------------------------------------------
2. PHYSICAL STRUCTURE & CORE COMPONENTS
--------------------------------------------------------------------------------
The PAAA-U chip layout is perfectly symmetrical and circular, eliminating spatial
asymmetries and signal propagation skew.

A. The Core Vector Transmitter (CVT):
- Positioned at the absolute geometric center ($r = 0$).
- Consists of a monolithic, high-density Circular Optical Phased Array (COPA).
- Dynamically steers and modulates coherent laser beams ($650\text{ nm}$
optimized active wavelength) across a full $360^\circ$ planar field
without any micro-mechanical components.

B. The Interference Matrix Ring (IMR):
- A series of concentric micro-ring resonators and optical waveguides
etched from high-index contrast material (Silicon Nitride, $\text{Si}_3\text{N}_4$
on Silicon Dioxide, $\text{SiO}_2$).
- Functions as the physical medium where matrix weights are statically or
dynamically mapped through phase-shifting nano-structures.

C. The Peripheral Photo-Receptor Array (PPRA):
- Positioned at the outermost boundary of the disc ($r = R$).
- A ring of ultra-fast Germanium-on-Silicon (Ge-on-Si) photodiodes with
integrated transimpedance amplifiers (TIAs) to capture output signals.

--------------------------------------------------------------------------------
3. MATHEMATICAL AND PHYSICS FOUNDATION
--------------------------------------------------------------------------------
The core of AI computing relies on Matrix-Vector Multiplications (MVM). PAAA-U
solves these operations natively at the speed of light through the principle of
**Optical Interference and Superposition**.

### 3.1 Wave Equation & Phase Steering
A light wave emitted by the central CVT towards a specific angular coordinate
$\theta$ on the ring can be mathematically represented as a complex scalar field:

$$E(r, \theta, t) = A(\theta) \cdot e^{i(\mathbf{k} \cdot \mathbf{r} - \omega t + \phi(\theta))}$$

Where:
- $A(\theta)$ is the initial amplitude vector.
- $\mathbf{k}$ is the wave vector ($|\mathbf{k}| = \frac{2\pi n}{\lambda}$).
- $\omega$ is the angular frequency of the light source.
- $\phi(\theta)$ is the electronically controlled phase offset applied by the
central Phased Array.

By precisely tuning the phase distribution $\phi(\theta)$ at the central core,
constructive interference can be dynamically targeted to any coordinate on the
outer matrix ring without changing physical geometries:

$$\Delta \phi = \mathbf{k} \cdot \Delta \mathbf{r}$$

### 3.2 Matrix-Vector Multiplication (MVM) through Interference
Let the input vector to a neural network layer be mapped onto the amplitudes and
phases of the emitted light rays $\mathbf{X} = [x_1, x_2, \dots, x_n]^T$.
The synaptic weight matrix $\mathbf{W}$ is mapped onto the localized phase-shifting
attenuators within the ASIC Ring.

When multiple coherent light beams converge at a single peripheral photoreceptor
node $y_j$ at the radius $R$, their optical fields sum up linearly:

$$E_{out}(R, \theta_j) = \sum_{i=1}^{n} w_{ji} \cdot x_i$$

Where $w_{ji} = a_{ji} \cdot e^{i\Delta \phi_{ji}}$ represents the complex optical
weight (attenuation $a_{ji}$ and phase delay $\Delta \phi_{ji}$).

The square-law photodetector measures the optical intensity $I$, which inherently
performs the absolute square of the field summation, providing a built-in
non-linear function mapping:

$$I(\theta_j) = |E_{out}(R, \theta_j)|^2 = \left| \sum_{i=1}^{n} w_{ji} \cdot x_i \right|^2$$

This physical interaction maps perfectly to the core operational primitives of
Large Language Models (LLMs) and Transformer attention mechanisms:

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

In the PAAA-U architecture, the dot-product $QK^T$ is calculated in a single
optical flight pass across the radius $R$ of the circular core.

--------------------------------------------------------------------------------
4. SIGNAL PROPAGATION MATRIX AND LOGIC FLOW
--------------------------------------------------------------------------------

### 4.1 Layout Matrix Specification
The architectural configuration maps spatial layout directly to computing layers:
* Inner Radius Matrix ($r = 0$ to $r = 0.1R$): Electromagnetic field control layer housing the Core Vector Transmitter (CVT) sub-arrays.
* Intermediate Compute Matrix ($r = 0.1R$ to $r = 0.9R$): Concentric wave modulation lanes configured as the active Interference Matrix Ring (IMR).
* Boundary Detection Matrix ($r = 0.9R$ to $r = R$): High-sensitivity photon termination zones mapped to the Peripheral Photo-Receptor Array (PPRA).

### 4.2 Step-by-Step Execution Sequence
1. **DATA INPUT (Electrical Domain):** Digital AI Tensors (Tokens/Embeddings) are processed through high-speed DAC Converters to form raw driving voltage waves.
2. **ELECTRO-OPTIC MODULATION (CVT at $r=0$):** Electrical signals drive the central Circular Optical Phased Array, mapping numerical tensor values directly into Phase ($\phi$) and Amplitude ($A$) profiles of coherent light.
3. **FLIGHT DOMAIN LUMINANCE ($0 < r < R$):** Light waves propagate radially outward in a uniform, symmetrical 360-degree wave front, traveling through the substrate medium at pure optical speed ($v = \frac{c}{n} \approx 200,000,000\text{ m/s}$).
4. **PHOTONIC COMPUTATION (The ASIC Ring):** Symmetrically traveling waves intersect, overlap, and collide inside the etched micro-ring waveguide matrix. Physical Constructive and Destructive Interference calculates dense Matrix Multiplication instantly.
5. **DETECTION & NON-LINEARITY (PPRA at $r=R$):** The boundary photoreceptors read the cumulative wave intensities. The physical square-law property of photodiode detection natively executes the mathematical non-linear activation mapping.
6. **DATA OUTPUT (Electrical Domain):** Ultrafast Transimpedance Amplifiers (TIAs) convert the resultant currents back into clear electrical signals, streaming processed tensors to the host system or cascading directly into the next optical layer ring.

--------------------------------------------------------------------------------
5. BREAKTHROUGH ADVANTAGES & METRICS
--------------------------------------------------------------------------------
- **True Zero Joule Compute:** Because photons do not possess electrical charge,
they pass through the waveguide pathways without causing electron scattering.
Thermal dissipation within the compute fabric is effectively zero ($0\text{ W}$
dynamic heat output during execution).
- **Infinite Bus Bandwidth:** Utilizing Wavelength-Division Multiplexing (WDM),
different colors of light (different laser wavelengths $\lambda_1, \lambda_2, \dots$)
can occupy the exact same physical space within the circular core simultaneously
without signal collisions, providing near-infinite parallel data processing.
- **Latency Fixed by Geometry:** The calculation latency $\tau$ is strictly
bound by the physical radius of the chip $R$ divided by the speed of light
in the medium ($v$):

$$\tau = \frac{R}{v} = \frac{R \cdot n}{c}$$

For a chip radius of $R = 10\text{ mm}$ and a refractive index of $n = 2.0$,
the execution time for an entire layer calculation is exactly $\approx 66.7\text{ picoseconds}$.

--------------------------------------------------------------------------------

# AUTHOR: JUHO ARTTURI HEMMINKI
