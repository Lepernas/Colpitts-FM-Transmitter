# Single-Transistor VHF Colpitts FM Transmitter

A compact, short-range Frequency Modulation (FM) transmitter built using a single general-purpose NPN transistor (BC547). The circuit functions simultaneously as an audio preamplifier/modulator and an RF oscillator operating within the standard FM broadcast band (88–108 MHz).

The prototype was constructed using the **"Dead-Bug / Manhattan" free-form soldering technique** directly on a solid copper clad board to provide an ultra-low impedance RF ground plane and eliminate parasitic capacitances.

---

## 📸 Prototype Showcase

<!-- Fotoğrafları repoya yükledikten sonra isimlerini aşağıdaki dosyalarla eşleştirebilirsiniz -->
<p align="center">
  <img src="circuit_prototype.jpg" alt="FM Transmitter Dead-Bug Assembly" width="550">
</p>

---

## ⚡ Technical Specifications

* **Operating Frequency:** 101.0 MHz (Verified on FM Broadcast Spectrum)
* **Oscillator Topology:** Single-stage Colpitts RF Oscillator
* **Modulation Scheme:** Direct Frequency Modulation (Reactance modulation via base-collector junction capacitance)
* **Active Element:** BC547B NPN Bipolar Junction Transistor (BJT)
* **Supply Voltage:** 3.0 V DC (CR2025 / CR2032 Lithium Coin Cell)
* **Current Consumption:** ~20 mA at 3.0 V
* **Antenna Setup:** ~15 cm flexible jumper wire (acting as a shortened monopole radiator)
* **Tested Transmission Range:** Direct laboratory desk verification (~0.5 m LOS to receiver antenna)
* **Grounding Scheme:** Continuous ground plane on single-sided copper laminate

---

## 📐 Circuit Schematic

<p align="center">
  <img src="schematic.jpeg" alt="Proteus Circuit Schematic" width="750">
</p>

*SPICE/Proteus simulation schematic showing the Colpitts oscillator core, audio coupling network, and RF tank configuration.*

---

## 🔧 Component List (BOM)

| Component | Value / Part Number | Description / Function |
| :--- | :--- | :--- |
| **Q1** | BC547 | RF Oscillator & Active Modulator |
| **MIC1** | Electret Microphone | 2-pin acoustic transducer |
| **R1, R2** | 10 kΩ | Microphone bias & Transistor base pull-up resistor |
| **R3** | 220 Ω | Emitter stabilization resistor (connected to GND) |
| **C1** | 100 nF (Film 104) | Audio DC-blocking coupling capacitor |
| **C2** | 1 nF (Film 1nK100) | Base RF bypass to ground |
| **C3** | 27 pF (Ceramic) | Emitter bypass / Tank divider |
| **C4, C5** | 100 nF (Film 104) | Supply rail RF decoupling capacitors |
| **C6** | 10 pF (Ceramic) | Collector-to-Emitter Colpitts feedback capacitor |
| **C7** | 4–30 pF (Blue Trimmer) | Variable carrier frequency tuning capacitor |
| **C8** | 5.6 pF (Ceramic) | Antenna output isolation / coupling capacitor |
| **L1** | ~0.1 µH (Hand-wound) | 4 turns, 0.8 mm enameled copper wire, 4–5 mm core |
| **Power** | 3.0 V Battery | CR2025 coin cell with soldered clip holder |
| **Substrate** | Copper Clad Board | Unetched PCB used as structural chassis and RF GND |

---

## 🛠️ Design & Prototyping Approach

### Why "Dead-Bug" on a Copper Clad Board?
At VHF frequencies (~100 MHz), standard solderless breadboards and generic perforated boards introduce substantial stray capacitance (2–5 pF per contact) and unpredictable lead inductance, which often degrades the tank's quality factor ($Q$) or prevents oscillation altogether.

* **Solid Ground Plane:** The entire unetched copper board acts as a universal low-impedance ground (0V reference), minimizing return loop inductances and RF noise.
* **Point-to-Point Mechanical Rigidity:** Component leads were kept as short as possible and soldered in mid-air ("dead bug" style), keeping high-frequency paths compact and predictable.
* **Frequency Tuning:** Coarse carrier adjustment is achieved mechanically by altering the spacing of the hand-wound coil turns, followed by fine tuning via the onboard trimmer capacitor using non-conductive tools.

---

## 🔬 Testing & Verification

1. The transmitter was powered via a fresh 3.0 V CR2025 button cell.
2. A portable analog FM receiver (equipped with an approximately 10 cm antenna) was positioned approximately 0.5 meters away on the test bench.
3. The carrier frequency was tuned to an empty spectrum slot at **101.0 MHz** using the trimmer capacitor.
4. Carrier quieting was established immediately upon reaching resonance, and acoustic transmission was confirmed with clear, hum-free voice pickup from the electret microphone capsule.
