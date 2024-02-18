# Wired direct communication from Device Gateway to Consolidated Monitoring Screen

## Context
The Nurse Station's Consolidated Monitoring Screen should promptly exhibit essential patient vital sign information, updating every second. This includes data sourced from eight distinct patient-monitoring devices connected to the Device Gateway: heart rate, blood pressure, oxygen level, blood sugar, respiration rate, electrocardiogram (ECG), body temperature, and sleep status.

## Status
Proposed

## Decision
To ensure swift data presentation, the choice was made to establish direct wired communication from the Device Gateway. The Device Gateway will transmit data as fire-and-forget messages, which the application on the Consolidated Monitoring Screen will then receive and display.

## Consequences
This form of communication is designed to guarantee immediate reception of input data, enabling medical professionals to promptly respond if necessary.
