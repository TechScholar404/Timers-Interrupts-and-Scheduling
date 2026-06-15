Laboratory Activity 1: Timers, Interrupts, and Task Scheduling
Course: BCA143 Firmware Programming
Student:Kate Alexia Pansoy
Date: June 2026

Project Description
This project demonstrates timer interrupts and task scheduling using the RT-Spark Development Board. Two hardware timers generate interrupts at different intervals to control LEDs and trigger tasks. An external button interrupt is also implemented to demonstrate event-triggered scheduling.

Hardware
 RT-Spark Development Board
 Red LED (PF11)
 Blue LED (PF12)
 User Button (PA0)
 Debug Pin (PE0)
Features
  TIM2: 1 Hz periodic interrupt (high priority)
  TIM3: 2 Hz periodic interrupt (medium priority)
  External interrupt on button press
   Foreground/background system architecture
  Timing measurement and analysis
Timing Measurements
  TRelease (TIM2): 1.0 second
  TLatency (Task A): 24.94 µs
  TISR (TIM2): 4.31 µs
  TTask (Task A): 50 ms
  TResponse (Task A): 50.02443 ms
Sequence Diagram
A sequence diagram illustrating the interaction between the timers, interrupts, button input, and main loop is included in the project documentation.

Build Instructions
  Open the project in STM32CubeIDE.
  Build the project using Project → Build All.
  Connect the RT-Spark board via USB.
  Upload and run the project using Run or Debug.
  Observe the LEDs blinking at different rates and test the button interrupt.
Analysis
  The system uses timer interrupts to execute tasks periodically.
  Interrupt-based scheduling provides faster response compared to polling.
  The foreground/background architecture allows multiple tasks to be managed efficiently.
   The button interrupt demonstrates event-triggered scheduling with immediate response.
References
Castor, P. R. P. (2025). Software Design Basics (Lecture 2). BCA143 Firmware Programming, MSU-IIT.
STMicroelectronics. (2024). STM32F4 HAL Driver User Manual.
