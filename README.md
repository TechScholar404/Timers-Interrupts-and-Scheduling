Here is a clean, well-structured, and professionally formatted version of your **README.md** file for your laboratory activity. It uses clear typography, structured tables, and code blocks to make it highly readable for instructors or peer reviewers.

---

# Laboratory Activity 1: Timers, Interrupts, and Task Scheduling

**Course:** BCA143 Firmware Programming

**Student:** Kate Alexia Pansoy

**Date:** June 2026

---

## 📝 Project Description

This project demonstrates the implementation of hardware timer interrupts and task scheduling using the **RT-Spark Development Board**. Two hardware timers are configured to generate periodic interrupts at different intervals to control onboard LEDs and trigger specific tasks. Additionally, an external button interrupt is implemented to demonstrate event-triggered scheduling within a foreground/background system architecture.

---

## 🛠️ Hardware Requirements

* **Development Board:** RT-Spark Development Board
* **Peripherals & Pins:**
* **Red LED:** `PF11`
* **Blue LED:** `PF12`
* **User Button:** `PA0` (External Interrupt)
* **Debug Pin:** `PE0`



---

## 🚀 Features

* **TIM2 Interrupt:** 1 Hz periodic interrupt configured with **High Priority**.
* **TIM3 Interrupt:** 2 Hz periodic interrupt configured with **Medium Priority**.
* **External Interrupt (EXTI):** Event-triggered task mapped to the user button press.
* **Architecture:** Foreground/Background system design for efficient task management.
* **Performance Analysis:** Embedded toggle pins used for precise timing measurement.

---

## 📊 Timing Measurements & Analysis

### Measurement Data

The following metrics were captured using a digital oscilloscope/logic analyzer via the debug pin:

| Parameter | Description | Measured Value |
| --- | --- | --- |
| $T_{\text{Release}}$ | TIM2 Interrupt Period | 1.0 second |
| $T_{\text{Latency}}$ | Interrupt Latency for Task A | 24.94 µs |
| $T_{\text{ISR}}$ | Time spent inside TIM2 ISR | 4.31 µs |
| $T_{\text{Task}}$ | Execution time of Task A | 50.00 ms |
| $T_{\text{Response}}$ | Total Response Time for Task A | 50.02443 ms |

### Key Findings

* **Deterministic Scheduling:** The system utilizes dedicated hardware timer interrupts to execute periodic tasks, ensuring highly predictable execution windows.
* **Efficiency:** Interrupt-based scheduling significantly reduces CPU overhead and provides drastically faster response times compared to traditional polling methods.
* **Concurrency:** The foreground/background architecture successfully manages asynchronous external events (button presses) alongside deterministic background tasks without missing critical deadlines.

---

## 🗺️ System Architecture & Sequence

```
[Hardware Timers / Button] 
       │ (Interrupt Triggers)
       ▼
 [Interrupt Service Routines (ISR)] ──(Sets Flags / Toggles LEDs)──► [Foreground]
       │
       ▼
 [Main Loop (Background Poll)] ───────(Executes Heavy Tasks)──────► [Background]

```

> 📌 **Note:** A detailed sequence diagram illustrating the exact timing interaction between `TIM2`, `TIM3`, the `PA0` button input, and the `main()` background loop is included in the accompanying project documentation folder.

---

## 💻 Build & Deployment Instructions

Follow these steps to set up, compile, and flash the project:

1. **Open the Project**
* Launch **STM32CubeIDE**.
* Import or open the project workspace.


2. **Build the Source Code**
* Navigate to the top menu and select `Project` ➔ `Build All` (or press `Ctrl + B`).
* Verify that the compilation finishes with `0 errors`.


3. **Hardware Connection**
* Connect the **RT-Spark Development Board** to your PC using a USB cable.
* Ensure the onboard debugger is recognized.


4. **Flash and Run**
* Click on `Run` ➔ `Run` (or `Debug` to step through the code).


5. **Verification**
* Observe the **Red LED (PF11)** and **Blue LED (PF12)** blinking at their respective 1 Hz and 2 Hz rates.
* Press the **User Button (PA0)** to verify the event-triggered interrupt behavior.
   The button interrupt demonstrates event-triggered scheduling with immediate response.
References
Castor, P. R. P. (2025). Software Design Basics (Lecture 2). BCA143 Firmware Programming, MSU-IIT.
STMicroelectronics. (2024). STM32F4 HAL Driver User Manual.
