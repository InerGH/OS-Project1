# Green Scheduler – CPU Scheduling Simulation Using Dynamic Voltage and Frequency Scaling (DVFS)

## Overview

This project simulates an energy-efficient CPU scheduler based on the concept of **Dynamic Voltage and Frequency Scaling (DVFS)**. The goal is to compare how a standard CPU scheduling algorithm (such as Round Robin) performs against a DVFS-enabled scheduler that dynamically adjusts CPU performance levels according to system load. The project demonstrates the trade-off between energy consumption and process turnaround performance.

This work is developed as part of the **Operating Systems** course, focusing on process scheduling, CPU utilization, and energy efficiency.

## Objectives

* Implement a baseline CPU scheduling algorithm (Round Robin).
* Design a DVFS-based energy-efficient scheduler that reduces simulated power usage under low load.
* Compare both schedulers based on:

  * Average waiting time
  * Turnaround time
  * CPU utilization
  * Simulated energy consumption
* Visualize performance and energy metrics using tables or plots.

## Concept

DVFS is a power management method that reduces CPU **voltage** and **frequency** during low computational demand. Because CPU power is approximately proportional to `V^2 * f`, reducing these parameters significantly lowers energy use while slightly increasing task completion time. In this project, DVFS is simulated by modeling three CPU operating states:

| State            | Frequency (f) | Voltage (V) | Relative Power |
| ---------------- | ------------- | ----------- | -------------- |
| High Performance | 1.0           | 1.0         | 1.00           |
| Balanced         | 0.75          | 0.85        | 0.54           |
| Eco Mode         | 0.5           | 0.7         | 0.25           |

The scheduler transitions between these states depending on the current system load:

* **High Performance**: Active when multiple processes are in the ready queue.
* **Balanced**: Used when moderate load is detected.
* **Eco Mode**: Triggered during idle or light load conditions.

## Methodology

1. **Input**: The simulator accepts a set of processes with arrival time, burst time, and (optionally) energy rate.
2. **Scheduling**:

   * Implement a Round Robin scheduler as the baseline.
   * Implement a Green Scheduler that applies DVFS dynamically during execution.
3. **Energy Calculation**:

   * Power = `V^2 * f`
   * Energy = `Power * ExecutionTime`
   * Burst durations are scaled inversely to frequency (lower frequency means longer execution time).
4. **Comparison**:

   * Measure total energy used, turnaround time, and waiting time.
   * Produce tabular or graphical comparison results.

## Example Output

| Metric                  | Round Robin | DVFS Scheduler |
| ----------------------- | ----------- | -------------- |
| Average Waiting Time    | 6.2         | 6.8            |
| Average Turnaround Time | 10.5        | 11.0           |
| Total Energy Used       | 1250 units  | 780 units      |
| Energy Saved            | -           | 38%            |

The results illustrate that energy-efficient scheduling can achieve substantial energy savings with minimal performance degradation.

## Tools and Technologies

* **Programming Language:** Python 3
* **Libraries:** matplotlib (for visualization), tabulate (for result formatting)
* **Platform:** Cross-platform (works in any Python environment)

## Implementation Plan

1. Define a `Process` class (arrival time, burst time, remaining time).
2. Create a Round Robin scheduler for baseline comparison.
3. Implement DVFS logic and integrate it into the scheduler loop.
4. Collect and compute performance and energy metrics.
5. Generate tables or charts comparing both approaches.

## Expected Outcomes

* Demonstration of DVFS concept through software simulation.
* Quantitative comparison between traditional and energy-efficient scheduling.
* Visualization of energy-time trade-offs in CPU scheduling.

## Future Work

* Add dynamic frequency scaling curves for finer-grained control.
* Incorporate real-world TDP (Thermal Design Power) data for realistic modeling.
* Extend the model to support multi-core scheduling and dynamic process migration.

## Author

**Iner Hasanović**
International University of Sarajevo
Operating Systems Project – November 2025

