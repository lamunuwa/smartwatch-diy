ExpWatch BETA 
**Version:** v1.0.0 BETA
**Type:** Academic Project / First Fabricated Prototype  

---

## 1. Project Context

This project was developed as a **multidisciplinary academic initiative**, integrating knowledge in:

- PCB design  
- Embedded systems  
- Programming (C and MicroPython)  
- Basic instrumentation  

The main goal is to create a **functional, simple, and scalable prototype** that helps understand how compact devices such as smartwatches (~35 mm) integrate multiple subsystems.

Target features include:

- Basic vital signs measurement (heart rate and SpO₂)  
- Real-time clock functionality  
- Alarm system  
- Basic user interface  

This version corresponds to:

> **v1.0.0 – First iteration sent to manufacturing**

---

## 2. Design Constraints

The design was heavily influenced by practical limitations:

### 2.1 Component Availability

Many design decisions were driven by the availability of components in the laboratory.

A key example is the use of **0805 passive components**, whereas a more optimized design would use **0603 or 0402** packages to reduce board size.

This decision directly impacts PCB density and overall dimensions.

---

### 2.2 Physical Constraints

The initial target size was **30 mm × 30 mm**, aiming to approach commercial smartwatch dimensions.

In practice, the final size was determined by:

- Available component sizes  
- Use of prebuilt modules  
- Larger-than-ideal package choices  

---

### 2.3 Academic Requirements

The project had to meet specific course requirements:

- Use of **MicroPython and C**  
- Avoiding simplified environments such as Arduino (.ino)  

This directly influenced microcontroller selection.

---

### 2.4 Cost and Accessibility

Priority was given to solutions that are:

- Low-cost  
- Easily available  
- Well documented  

This led to the use of **commercial modules** instead of fully discrete implementations.

---

## 3. Power System

### 3.1 Battery

Selected battery:

- **Li-Po 402030**  
- **3.7 V**  
- **200 mAh**

**Justification:**

- Compatible with available dimensions (~35 mm)  
- Sufficient capacity for demonstration purposes  

**Estimated autonomy:**

- **6 to 8 hours**, depending on usage  

---

### 3.2 Power Consumption

Estimated system consumption:

- ~**100 mA** (However, the vibration motor is intended for short-term alarms)  
- ~**24 mA** (MCU)  
- Additional **µA-level consumption**, considered negligible  

---

### 3.3 Charging and Protection

The design uses:

- **TP4056** (charger)  
- **DW01A** (protection IC)  
- **FS8205** (dual MOSFET)

**Justification:**

- Widely used and well-proven circuit  
- Low cost  
- Extensive documentation  

**Space optimization:**

A **SOT-23 version of the FS8205** was used instead of TSSOP-8, as system current does not require a larger package.

---

## 4. Voltage Regulation

The design uses:

- **AMS1117-3.3**

**Limitations:**

- Low efficiency  
- High quiescent current  
- Large physical size  
- Considered outdated  

**Reason for use:**

- Availability in the laboratory  

**Future improvement:**

- Replace with modern LDOs such as **HT7333**

---

## 5. Processing Unit

### 5.1 Microcontroller

Selected MCU:

- **RP2040**

**Initial alternative:**

- ATmega328P  

**Reason for change:**

- Academic requirement to use **MicroPython + C**  

**Final justification:**

- Flexibility  
- Meets course requirements  
- Suitable form factor  

---

### 5.2 External Memory

- **W25Q16JVUXIQ**

**Reason:**

- Direct compatibility with RP2040  
- Availability as a paired component  

---

## 6. Functional Modules

The system aims to replicate basic smartwatch functionality.

---

### 6.1 Heart Rate and SpO₂ Sensor

Two approaches were considered:

- Custom analog front-end (op-amps + filters)  
- Raw chip (Raw MAX30100)
- Integrated module (MAX30100 I2C outputs)

**Final decision:**

- **Integrated module - MAX30100 I2C outputs**  

**Justification:**

- Reduced design complexity  
- Higher robustness against noise  
- Lower implementation risk  
- Better cost-performance ratio  

---

### 6.2 Real-Time Clock (RTC)

- **DS3231MZ**

**Justification:**

- Sufficient accuracy for prototype  
- Low cost  
- Integrated alarms  

---

### 6.3 Alert System

- Coin vibration motor  

**Justification:**

- Compact size  
- Simple control
- Relatively low consumption 

---

### 6.4 User Interface

- I2C OLED display  

**Justification:**

- Available in the laboratory  
- Easy integration  

**Future improvements:**

- Circular display  
- SPI interface  
- Touch input  

---

## 7. Design Approach

This version prioritizes:

- Functionality over optimization  
- Availability over ideal component selection  
- Simplicity over full integration  

It is intended as a **first functional iteration** to validate concepts.

---

## 8. Future Improvements

- Maximize PCB size using smaller SMD packages  
- Replace inefficient voltage regulator  
- Integrate sensors at IC level instead of modules  
- Improve power efficiency  
- Enhance user interface  

---

## 9. Project Scope

This version (v1.0.0 BETA) is not intended as a final or production-ready design.

It represents an academic deliverable, where several design decisions were made based on component availability, time constraints, and course requirements rather than optimal engineering practices.

This version serves as a functional baseline for those improvements.