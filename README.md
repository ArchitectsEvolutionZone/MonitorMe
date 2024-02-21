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

### [Client Initial requirements](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/ClientInitialRequirements.md)

### [Requirements analysis](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/Capabilities.md)

<img src="https://wpforms.com/wp-content/uploads/2021/10/user-journey.png" align="left" height="64px" />

- [User journey - hospital admin](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/UserJourneys/HospitalAdmin.md)
- [User journey - medical profesional](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/UserJourneys/MedicalProfessional.md)
- [Requirements analysis conclusions](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/Core%20requirements.md)

<img src="https://www.techwell.com/sites/default/files/stories/images/cropped_teasers/Beth%20Romanik/2018/requirements-software-obsolete.png" align="right" height="64px" />

### [Cross-functional requirements](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/Cross%20Functional%20Requirements.png)
In the project's requirement phase, cross-functional requirements were pinpointed. These characteristics served as guiding principles for the team's choices throughout the architecture analysis stage.

| Top 3      | Driving characteristics       | Details |
|----------------|----------------|----------------|
| [  ] | Availability |Ensuring a robust system uptime is imperative to promptly dispatch alerts, particularly when dealing with vital signs. This is enforced by reducing the number of possible points of failure and by implementing a failover mechanism that automatically switches to backup systems or resources when the primary ones experience issues, ensuring uninterrupted service. Also regularly data will be backed up to prevent loss.|
| [x] | Fault tolerance |In the event of critical errors occurring with any of the vital sign devices, the remaining components of the system must continue to operate seamlessly, ensuring ongoing monitoring of other vital signs. Robust monitoring tools will be used to detect faults or anomalies in real-time. Systems will be designed to gracefully degrade when faults occur, ensuring that essential services remain operational even if non-critical functionalities are affected. The faulty components will be isolated to prevent the failure from spreading throughout the system. The use of NoSQL database should enforce fault tolerance as well, since it will distribute data across multiple nodes, and can continue to operate even if some nodes fail.|
| [x] | Responsiveness | The medical professional utilizing the consolidated monitoring screen should gain an overview of the vital signs data collected from medical devices within a timeframe of 1 second or less. One of the ways to achieve a short timeframe for the user to have a response, is to have in place a wired connection from the Device Gateway that's connected to the medical devices, to the Consolidated Monitoring Screen. This should ensure a very fast communication. The communication will be done asynchronously, by using a Message-Queuing software. |
| [ ] |Extensibility|   StayHealthy, Inc. is considering the addition of more vital sign monitoring devices to enhance the capabilities of MonitorMe in the future. In order to have extensibility, the connectivity with the monitoring medical devices will be made at plugin level. Thus, every new device or version added in the future, will represent a new plugin. |
|[ ]| Agility |We plan to adapt to rapidly changing of the business requirements, as they learn more about the new market, by  adopting an iterative and incremental development methodology, like Scrum. This will allow for continuous improvement and flexibility in responding to changing requirements. Understanding and meeting the needs of customers will get prioritized and fast feedback will be gathered and used to iterate on new functionalities quickly.|
|[x]| Performance	| The component of the system responsible for analyzing vital sign data plays a pivotal role in responding promptly. It is critical for swift and timely action, facilitating instant alerts to medical professionals. One measures taken to achieve performance, will be to optimize algorithms and data structures to ensure efficient processing and resource utilization. Also a caching mechanism will be put in place to store frequently accessed data, reducing the need for redundant processing and enhancing response times.|
|[ ]	|Accuracy|	Vital sign data that is analyzed and recorded must be as accurate as possible since human lives are at stake. Data sources will be validated and verified to minimize the risk of errors from the outset. Also quality assurance and testing processes will be integrated in order to identify and rectify inaccuracies in data, software, or processes before they impact outcomes. This includes leveraging automation and technology to perform repetitive and data-intensive tasks, reducing the likelihood of human errors and enhancing overall accuracy.|

Other characteristics taken into consideration were:

- interoperability - since we have different systems that need to communicate, exchange data, and operate in conjunction with one another, we need to focus also on interoperability. We will do this by implementing widely accepted industry standards for data formats, communication protocols (HL7), and interfaces. Data formats and structures will be standardized to ensure uniformity in how information is represented and exchanged.
- redundancy - for minimizing the risk of system failure, we will involve the duplication of critical a component, that is the on-premise server, to enhance reliability and minimize the risk of system failure.
- confidentiality - patient data is sensitive data and needs to be protected. This involves implementing security measures like encryption techniques, access controls, and policies to protect it from being disclosed to unauthorized individuals or entities.

Implicit characteristics:

- feasibility - we will focus on taking feasibility-driven architectural decisions, which aim to strike a balance between achieving the desired functionality and meeting project constraints. We will also ensure that the chosen architecture is viable within the given time and budgetary constraints while utilizing the available developer skills effectively.
- security - is a critical consideration for our system, particularly given its involvement with patient vital data. To bolster security measures, the implementation of both wired and WLAN communication between systems has been adopted. This dual approach aims to provide a resilient and secure network infrastructure. Additionally, the use of devices adhering to established data communication standards, such as HL7, has been prioritized. Opting for standardized protocols over proprietary ones not only fosters interoperability but also contributes to a more secure and cost-effective system. The decision to host the server on-premise further enhances security. This localized approach allows for greater control over access, monitoring, and safeguarding of sensitive patient information. The combination of these measures underscores the commitment to maintaining the integrity and confidentiality of patient vital data throughout the system architecture.
- maintainability - we will strive for designing the system with a modular structure, where components are independent and loosely coupled. This facilitates easier updates or replacements without affecting the entire system, since we will need to address new functionalities. Standardized coding practices and conventions across the development team will be enforced. Consistency in coding style makes it easier for multiple developers to understand and maintain the codebase. Automated testing will be implemented to validate the system's functionality after updates or modifications. Automated tests help catch issues early, ensuring that changes do not introduce unexpected problems. And also Continuous Integration and Deployment pipelines will be created to automate the testing and deployment processes. This accelerates the delivery of updates and ensures a more streamlined and predictable maintenance workflow.
- observability - there will be in place a systematic monitoring and logging of various aspects of the system that will allow developers and operators to understand its functioning, diagnose issues, and optimize performance. 

## Architecture visualization
#### [OnPremise infrastructure](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/2.ArchitectureVisualization/Infrastructure.md)
#### [C4 diagram](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/2.ArchitectureVisualization/C4Diagram.md)
#### [Deployment](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/2.ArchitectureVisualization/Deployment.md)
## ADR
#### [ADR001](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/3.ADR/ADR001.md)

