Here is a simplified, minimal version of the README file for **Princess Dianne Estores**. It strips away the extra analysis text and keeps it clean, direct, and incredibly easy to read.

---

# Laboratory Activity 1: Timers, Interrupts, and Task Scheduling

**Course:** BCA143 Firmware Programming

**Student:** Princess Dianne Estores

**Date:** June 2026

---

## 📝 Project Description

This project demonstrates timer interrupts and task scheduling using the **RT-Spark Development Board**. Two hardware timers generate periodic interrupts to control LEDs and trigger tasks, while an external button interrupt handles event-triggered scheduling.

---

## 🛠️ Hardware

* **Board:** RT-Spark Development Board
* **Red LED:** `PF11`
* **Blue LED:** `PF12`
* **User Button:** `PA0`
* **Debug Pin:** `PE0`

---

## 🚀 Features

* **TIM2:** 1 Hz periodic interrupt (High Priority)
* **TIM3:** 2 Hz periodic interrupt (Medium Priority)
* **External Interrupt:** Triggered on user button press
* **Architecture:** Foreground / Background system architecture
* **Analysis:** Timing measurement and analysis

---

## 📊 Timing Measurements

| Parameter | Metric | Measured Value |
| --- | --- | --- |
| $T_{\text{Release}}$ | TIM2 Interrupt Period | 1.0 second |
| $T_{\text{Latency}}$ | Interrupt Latency (Task A) | 24.94 µs |
| $T_{\text{ISR}}$ | Time spent inside TIM2 ISR | 4.31 µs |
| $T_{\text{Task}}$ | Execution time of Task A | 50.00 ms |
| $T_{\text{Response}}$ | Total Response Time (Task A) | 50.02443 ms |

---

## 🗺️ Sequence Diagram

A sequence diagram illustrating the interactions between the timers, interrupts, button input, and main loop is included in the project documentation folder.

---

## 💻 Build Instructions

1. Open the project in **STM32CubeIDE**.
2. Build the project: Go to `Project` ➔ `Build All`.
3. Connect the **RT-Spark Board** to your PC via USB.
4. Upload and run the project using **Run** or **Debug**.
5. Observe the LEDs blinking and test the button interrupt.

---

## 🔍 Analysis

* The system uses timer interrupts to execute tasks periodically.
* Interrupt-based scheduling provides a faster response compared to polling.
* The foreground/background architecture allows multiple tasks to be managed efficiently.
* The button interrupt demonstrates event-triggered scheduling with an immediate response.

---

## 📚 References

1. Castor, P. R. P. (2025). *Software Design Basics (Lecture 2)*. BCA143 Firmware Programming, MSU-IIT.
2. STMicroelectronics. (2024). *STM32F4 HAL Driver User Manual*.
