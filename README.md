# Laboratory Activity 1: Timers, Interrupts, and Task Scheduling

**Course:** BCA143 Firmware Programming

**Student:** Kate Alexia Pansoy

**Date:** June 2026

---

## Project Description

This project implements timer-based interrupts and a cyclic executive scheduler on the **STM32F407ZGT6** microcontroller utilizing the **RT-Thread RT-Spark Development Board**. The system is designed to handle periodic and asynchronous tasks efficiently using a foreground/background architecture.

---

##  Hardware Specifications

* **Development Board:** RT-Thread RT-Spark (STM32F407ZGT6)
* **Peripherals & Pin Mapping:**
* **Red LED:** `PF11`
* **Blue LED:** `PF12`
* **User Button:** `PA0` (External Interrupt / EXTI)
* **Debug Pin:** `PE0` (Used for timing analysis via Logic Analyzer/Oscilloscope)



---

##  System Features

* **TIM2 Periodic Interrupt:** Configured at **1 Hz** with **High Priority**.
* **TIM3 Periodic Interrupt:** Configured at **2 Hz** with **Medium Priority**.
* **External Interrupt (EXTI):** Triggered asynchronously by the user button press (`PA0`).
* **Architecture:** Foreground (ISRs for time-critical events) / Background (Main cyclic executive loop) system design.
* **Analysis:** Real-time timing measurement using physical GPIO toggling on the debug pin.

---

##  Timing Measurements

| Parameter | Description | Target Value / Interval | Measured Value |
| --- | --- | --- | --- |
| $T_{\text{Release}}$ | TIM2 Interrupt Period | 1.0 second | *[Insert Value]* |
| $T_{\text{Latency}}$ | Interrupt Latency (Task A) | As quick as possible | *[Insert Value]* |
| $T_{\text{ISR}}$ | Time spent inside TIM2 ISR | Minimal overhead | *[Insert Value]* |
| $T_{\text{Task}}$ | Execution time of Task A | Process dependent | *[Insert Value]* |
| $T_{\text{Response}}$ | Total Response Time (Task A) | $T_{\text{Latency}} + T_{\text{Task}}$ | *[Insert Value]* |

---

## System Architecture

```
       ┌────────────────────────────────────────────────────────┐
       │                HARDWARE INTERRUPTS                     │
       │  (TIM2 @ 1Hz)      (TIM3 @ 2Hz)     (Button Press PA0) │
       └───────┬─────────────────┬────────────────────┬─────────┘
               │                 │                    │
               ▼                 ▼                    ▼
       ┌────────────────────────────────────────────────────────┐
       │           FOREGROUND: ISR Execution                    │
       │   - Toggle Debug Pins     - Set Task Flags             │
       └─────────────────────────┬──────────────────────────────┘
                                 │
                                 ▼ (Flags Passed)
       ┌────────────────────────────────────────────────────────┐
       │           BACKGROUND: Cyclic Main Loop                 │
       │   - Poll Flags            - Execute Delayed Tasks      │
       └────────────────────────────────────────────────────────┘


##  Build Instructions

1. **Open Workspace**
* Launch **STM32CubeIDE** and import the project folder.


2. **Compile Project**
* Navigate to `Project` ➔ `Build All` (or press `Ctrl + B`). Ensure there are `0 errors`.


3. **Hardware Setup**
* Connect the **RT-Thread RT-Spark Board** to your computer via USB.


4. **Flash Microcontroller**
* Click `Run` or `Debug` to upload the compiled binary file to the STM32F407ZGT6 target.


5. **Observation & Verification**
* Confirm the Red LED (`PF11`) blinks at **1 Hz** and the Blue LED (`PF12`) blinks at **2 Hz**.
* Press the User Button (`PA0`) to verify the event-triggered external interrupt handler execution.



---

## 📚 References

* Castor, P. R. P. (2026). *Software Design Basics (Lecture 2)*. BCA143 Firmware Programming, MSU-IIT.
