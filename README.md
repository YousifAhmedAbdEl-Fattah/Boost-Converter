<p align="center">
  <img src="https://img.shields.io/badge/Arduino-Nano-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/PWM-50kHz-brightgreen?style=for-the-badge">
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge">
  <img src="https://img.shields.io/badge/Power–Electronics-orange?style=for-the-badge">
</p>
<p align="center">
  <img src="images/Final_Project/Final_Project.JPG" alt="Boost Converter Project - AstraVolt" width="700">
</p>

# 🔌 Boost Converter Project – AstraVolt

## 📌 Project Overview
This project presents the **design and implementation of an irreversible (asynchronous) DC–DC Boost Converter** as an **educational and practical power electronics system**.

The converter steps up a low DC input voltage to a higher regulated output voltage using:
- An inductor for energy storage  
- A MOSFET for high-frequency switching  
- A fast recovery diode  
- An output capacitor to reduce voltage ripple  

An **isolated gate driver (TLP250)** is used to safely interface the low-voltage control circuit (Arduino) with the high-power switching stage, improving electrical safety, noise immunity, and reliability.

---

## 🎯 Educational Objectives
This project helps learners understand:
- Inductor charging and discharging behavior  
- The effect of duty cycle on output voltage  
- Continuous Conduction Mode (CCM) operation  
- Practical component selection and real-world losses  
- The importance of isolated gate drivers  
- Voltage regulation using feedback control  

---

## ⚙️ System Architecture
The system consists of the following main blocks:
- Power Stage (Boost Converter)
- Isolated Gate Driver (TLP250)
- Control Unit (Arduino Nano)
- Measurement Circuit (INA219 + Voltage Divider)
- User Interface (LCD + Potentiometer)
<p align="center">
  <kbd>
    <img src="images/System_Architecture.PNG" width="700">
  </kbd>
</p>

## 🧩 Main Components

### 🔋 Power Stage Components
| Component | Description |
|---------|-------------|
| Inductor | 40 mH |
| MOSFET | IRFP260 / FQPF20N60 |
| Diode | BY399 Fast Recovery |
| Output Capacitor | 22 µF / 350 V |
| Heat Sink | TO-247 / TO-220F |

### 🧠 Control & Measurement
| Component | Function |
|---------|----------|
| Arduino Nano | PWM generation & control |
| TLP250 | Isolated MOSFET gate driver |
| INA219 | Current measurement |
| Voltage Divider | Voltage measurement |
| LCD 16×2 | Voltage & current display |
| Potentiometer | Duty cycle adjustment |

---

## 🔄 Boost Converter Operating Principle

### 🔹 Mode 1: Switch ON – Energy Storage
- MOSFET is ON  
- Inductor stores energy  
- Diode is reverse-biased  
- Load is supplied by the output capacitor  

<p align="center">
  <kbd>
    <img src="images/Boost_Converter/second_operating_mode.png" width="600">
  </kbd>
</p>

---

### 🔹 Mode 2: Switch OFF – Energy Transfer
- MOSFET is OFF  
- Inductor releases stored energy  
- Diode conducts  
- Output voltage becomes higher than input voltage  

<p align="center">
  <kbd>
    <img src="images/Boost_Converter/Frist_operationg_mode.png" width="600">
  </kbd>
</p>

---

## 📐 Design Specifications
- **Input Voltage:** 12 V  
- **Output Voltage:** ≈ 34 V  
- **Switching Frequency:** 50 kHz  
- **Operating Mode:** CCM  
- **Control Method:** PWM with feedback  

---

## 📊 Design Summary
| Parameter | Value |
|---------|-------|
| Duty Cycle (Real) | 0.68 |
| Inductor | 40 mH |
| Peak Inductor Current | ≈ 3.55 A |
| Output Capacitor | 22 µF |
| Diode | BY399 |
| MOSFET | IRFP260 / FQPF20N60 |

---

## 🧮 Control & Firmware
The Arduino firmware performs the following tasks:
- Generates PWM at 50 kHz  
- Reads potentiometer to set duty cycle  
- Calculates theoretical output voltage  
- Measures actual voltage and current  
- Applies feedback control for voltage regulation  
- Displays data on LCD and Serial Monitor  

<p align="center">
  <a href="Arduino code/BoostConverter.ino">
    <kbd>
      <img src="https://ai.thestempedia.com/wp-content/uploads/2017/06/Arduino-Logo.png" width="200">
    </kbd>
  </a>
</p>
📌 *Click the image above to open the arduino code.*
---

## 🧪 Simulation

Simulation was performed using both **MATLAB (Simulink)** and **LTspice** to verify the boost converter operation before hardware implementation.

---

### 🔹 MATLAB (Simulink)

The MATLAB Simulink model represents the complete boost converter circuit and was used to analyze:
- Output voltage behavior  
- Inductor current waveform  
- Converter response to duty cycle changes  
<p align="center">
  <kbd>
    <img src="images/Sumlink_Simulation/Sumlink_Simulation.png" width="600">
  </kbd>
</p>

#### 🔸Waveform
<p align="center">
  <kbd>
    <img src="images/Sumlink_Simulation/Sumlink_waveform.PNG" width="600">
  </kbd>
</p>
---

### 🔹 LTspice

LTspice simulation was used to validate the switching behavior and observe detailed waveforms, including:
- Output voltage  
- Output voltage ripple  
- Inductor current  
- MOSFET and diode voltages
<p align="center">
  <a href="images/LTspice_Simulation">
    <kbd>
      <img src="https://sc.filehippo.net/images/t_app-icon-l/p/d55e21eb-857a-4b0e-8403-584ec5ce0543/3008849045/ltspice-logo" width="100">
    </kbd>
  </a>
</p>
📌 *Click the image above to open the LTspice Simulation.*
---

## 🧱 PCB Design

The PCB design of this project was developed using **EasyEDA** and is divided into two main sections:
1. **Isolated Gate Driver (TLP250)**
2. **Boost Converter Power Stage**

The separation improves safety, noise immunity, and overall system reliability.

---

### 🔹 Gate Driver PCB (TLP250)

The gate driver PCB provides **galvanic isolation** between the low-voltage control circuit (Arduino) and the high-power switching stage.  
It ensures clean gate signals, protects the controller, and reduces EMI.

#### 🔸 Gate Driver Schematic
<p align="center">
  <kbd>
    <img src="images/TLP250_Gate_Driver/Schematic_TLP250_Driver.png" width="700">
  </kbd>
</p>

#### 🔸 Gate Driver PCB Layout
<p align="center">
  <kbd>
    <img src="images/TLP250_Gate_Driver/PCB_TLP250_Driver.png" width="250">
  </kbd>
</p>

#### 🔸 Gate Driver 3D View
<p align="center">
  <kbd>
    <img src="images/TLP250_Gate_Driver/3D_PCB_TLP250_Driver.png" width="300">
  </kbd>
</p>

---

### 🔹 Boost Converter PCB

The boost converter PCB contains the **power stage components**, including the MOSFET, inductor, diode, and output capacitor.  
Special attention was given to:
- Short high-current paths  
- Proper grounding  
- Thermal performance  
- High-voltage clearance  

#### 🔸 Boost Converter Schematic
<p align="center">
  <kbd>
    <img src="images/Boost_Converter/Schematic_Boost_Converter.png" width="800">
  </kbd>
</p>

#### 🔸 Boost Converter PCB Layout
<p align="center">
  <kbd>
    <img src="images/Boost_Converter/PCB_Boost_Converter.png" width="600">
  </kbd>
</p>

#### 🔸 Boost Converter PCB 3D View
<p align="center">
  <kbd>
    <img src="images/Boost_Converter/3D_PCB_Boost_Converter2.png" width="600">
  </kbd>
</p>

---

## 🛠️ Final Assembled Hardware

This section shows the **final hardware implementation after complete soldering and assembly**.

All boards were fully assembled, interconnected, and tested as a complete working system.

---

### 🔹 Gate Driver Board (TLP250).
<p align="center">
  <kbd>
    <img src="images/TLP250_Gate_Driver/Final_TLP250_Gate_Driver.JPG">
  </kbd>
</p>

---

### 🔹 Boost Converter Board
<p align="center">
  <kbd>
    <img src="images/Boost_Converter/Final_Boost_Converter.jpeg" width="600">
  </kbd>
</p>

---

### 🔹 Complete System After Assembly
<p align="center">
  <kbd>
    <img src="images/Final_Project/Final_project2.jpeg" width="600">
  </kbd>
</p>

---


## 🧪 Testing & Results
- Tested at multiple duty cycle values
- Stable output voltage observed
- Real-time voltage and current monitoring
- Significant improvement after adding feedback control
## 📊 Experimental Test Results

The following table summarizes the experimental results using Vin=12.5 & R load = 10KΩ of the boost converter
under different duty cycle values.

| 🔁 Duty Cycle (%) | ⚡ Output Voltage (V) | 🔋 Output Current (mA) |
|------------------|----------------------|------------------------|
| 70%              | 42.5 V               | 357 mA                 |
| 60%              | 31.6 V               | 261 mA                 |
| 50%              | 24.7 V               | 353 mA                 |
| 30%              | 17.8 V               | 336 mA                 |
| 20%              | 15.3 V               | 328 mA                 |

The results confirm the expected relationship between **duty cycle and output voltage**,
with stable operation and consistent current behavior.

<p align="center">
  <kbd>
    <img src="images/Testing_and_anthor_data.png">
  </kbd>
</p>

---

## ⚠️ Challenges & Solutions

### MOSFET Availability Issue
- Some MOSFETs showed poor thermal and efficiency performance  
- **Solution:** Switched to FQPF20N60 (isolated package)

### Inductor Charging Issue
- High ripple and poor efficiency observed  
- **Solution:** Optimized inductance value and switching frequency

### Load Dependency Issue
- Output voltage varied with load changes  
- **Solution:** Implemented feedback control loop

---

## 🚀 Conclusion
This project demonstrates a **complete Boost Converter system**, covering:
**design → simulation → firmware → PCB → hardware testing**.

It provides a strong foundation for advanced power electronics designs such as:
- Synchronous boost converters  
- Isolated DC–DC converters  
- Advanced SMPS applications  

For more technical details, calculations, waveforms, and full documentation,  
please refer to the complete project report.

<p align="center">
  <a href="AstraVolta Report/AstraVolt Report.pdf">
    <kbd>
      <img src="images/AstraVolt_Logo.jpeg" width="300">
    </kbd>
  </a>
</p>

📌 *Click the image above to open the full project report.*

---
## 👥 Contributors

| Name | GitHub | Name | GitHub |
|------|--------|------|--------|
| Omar Salama | [@OmarSalama](https://github.com/Omar-Salama-1) | Omar Fetian | — |
| Omar Roman | — | Abdelrhaman Reda | — |
| Romissa Elhadidi | [@RomissaElhadidi](https://github.com/romisaaelhdaidi)|Hussein Aboalkheer| — |
| Renda Reka | — | —| — |

---
## 📜 License
This project is released under the  
**MIT License**.  
Use at your own risk.

---

## 🔖 Tags
`#BoostConverter` `#DCDC` `#PowerElectronics` `#Arduino` `#ArduinoNano`  
`#SMPS` `#PWM` `#TLP250` `#INA219` `#MOSFET`  
`#PCBDesign` `#EmbeddedSystems` `#HardwareProject` `#Electronics`
