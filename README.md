<img src="https://static.vecteezy.com/system/resources/previews/017/316/736/original/an-icon-of-health-monitor-in-modern-style-pulse-monitor-vector.jpg" align="right" height="64px" />

# MonitorMe

## Our story
<img src="https://clipart-library.com/8300/1931/description-clipart-description-clipart-1.jpg" align="left" height="64px" />

#### Context and Overview
StayHealthy, Inc. is a large successful medical software company that already has two popular cloud-based SAAS products on the market (MonitorThem and MyMedicalData).
The next product they want to bring to life is MonitorMe, a product that will collect patient vital signs from various sources (like wearables and medical devices that measure heart rate, blood pressure, oxygen level, blood sugar, respiration rate, electrocardiogram (ECG), body temperature, and sleep status). 
This document intends to describe the architecture of MonitorMe, constraints, and considerations for building an easy-to-use, reliable, scalable, and secure system.

<img src="https://i.pinimg.com/564x/18/f2/b7/18f2b7eee77761c7e1ab048b9fbf5d43.jpg" align="right" height="64px" />

#### Vision
MonitorMe will help medical professionals make informed decisions about a patient’s health state and treatments based on accurate and long-term measured vital signs, therefore increasing treatment accuracy, the likelihood of treatment success, and in the end patient experience, recovery time, and quality of life.
By creating a system that collects patient data, doctors and other medical professionals will be able to have a 360-degree view of patients'
In the future, patient data might be used to correlate various treatments, recovery patterns, and medical procedures with patient vital signs. (E.g. High blood sugar would not recommend a patient for “aaa” treatment because of “reason”), by taking advantage of the rapid AI development.

<img src="https://i.pinimg.com/564x/aa/ce/91/aace91f72298caaaf2c0eddcc61bd402.jpg" align="left" height="64px" />

#### The strategy
Our strategy is to create a system that will be able to accommodate and collect data from a wide range of medical devices and wearables, that can constantly increase the amount of data that we store for current and future use. Our architecture will focus on a fast display of patient’s vital signs, redundancy (not to lose vital signs captured from patients), and fast alerting of medical professionals. To achieve this, we envisioned a software system with the fewest steps possible from capturing vital signs to displaying them to a central nurse station. We also want to favor wired communication over wireless communication, hospitals usually have the infrastructure needed already in place.
To make sure we achieve an average response time of one second or less for displaying patient’s vital signs to a nurse station, we plan to have automated performance tests as soon as possible and to integrate them in the deployment pipeline. This way we can identify performance degradation from one build to another early on, enabling us to act and improve performance constantly.
To make the solution implementation more cost-effective, we will rely on standard protocols for capturing data from medical devices and wearables (e.g., Bluetooth LE for wearable devices, HL7 for medical devices). These standards will enable our system to connect to medical devices and wearable devices from a wide range of suppliers, significantly reducing the limitations on what hardware can be used with MonitorMe.

<img src="https://dailyasianage.com/library/1507488189_2.jpg" align="right" height="64px" />

#### Competitors and market analysis
The market for patient monitoring and vital signs devices is experiencing significant growth, driven by various factors including the increasing prevalence of chronic diseases, technological advancements in monitoring devices, and a growing emphasis on home healthcare. The global patient monitoring devices market was valued at USD 55.3 billion in 2023 and is expected to reach USD 92.8 billion by 2030, with a compound annual growth rate (CAGR) of 7.7% from 2023 to 2030. Multi-parameter patient monitoring devices, which integrate several vital signs into a single device, are particularly prominent due to their cost-effectiveness and comprehensive monitoring capabilities, making them increasingly significant in both hospital and home settings.
However, the growth of the vital signs monitoring market is somewhat tempered by the high cost associated with certain advanced monitoring products.
Overall, the market for patient and vital signs monitoring is robust and expanding, driven by healthcare needs, technological advancements, and a shift towards more convenient and cost-effective monitoring solutions.
Considering the above, there’s no surprise to find many players in this market (GE HealthCare, Medtronic, Vigilife, and Ascom, just to name a few), developing both hardware and software for patient bio-signs monitoring. This competition is good for the patients for the advancement in this field but puts a lot of pressure on companies that develop these software systems and devices. New software systems should aim to improve what already exists (from a performance and cost point of view) and to innovate further patient monitoring field.
A thorough analysis of competitors and products on the market is needed to ensure product-market fit and product-problem fit. By doing this we can also anticipate requirements beyond current ones.

## MonitorMe system overview

Familiarize youreself with the MonitorMe system. Find out how patients and hospital personel will interact with the system by going on the [user journeys](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/Capabilities.md) for each role.


This diagram presents an overview of the MonitorMe System functionalities 
<img src="https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/capabilities%20overview%203.png" />

Whereas this one illustrates the infrastructure that will be setup in the hospital for the MonitorMe System
<img src="https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/infrastructure.png"/>

## Requirements
#### [Functional requirements](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/Requirements/Functional%20Requirements.md)
#### [Cross-functional requirements](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/Requirements/Cross%20Functional%20Requirements.png)
## Architecture visualization
#### C4 diagram
#### User flows diagram
#### Deployment diagram
## ADR
#### [ADR001](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/ADR/ADR001.md)

