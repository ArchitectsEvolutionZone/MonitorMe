# Event-Driven chosen architecture Style

## Context
MonitorMe aims to provide instantaneous alerts to medical professionals by leveraging received vital data, enabling swift responses to potential problems with a patient. 
The system's core functionality revolves around real-time monitoring of vital signs, ensuring that healthcare providers receive timely notifications, facilitating prompt and 
effective interventions when necessary.

## Decision 
In the requirements analysis phase, the team identified Performance, Responsiveness, and Fault Tolerance as pivotal architectural characteristics for the MonitorMe system. 
Following an assessment using the Architecture Styles Worksheet, the team concluded that adopting an event-driven architecture would be the most suitable solution.

## Status
Proposed

## Consequences:

Real-time Responsiveness: Event-driven architectures excel at delivering real-time updates, aligning with the system's goal of monitoring vital signs promptly and providing instantaneous notifications to medical professionals.

Fault Tolerance Enhancement: The event-driven approach enhances fault tolerance by enabling the system to gracefully handle faults or disruptions, ensuring uninterrupted monitoring and alerting capabilities.

The decision to embrace an event-driven architecture for the MonitorMe system is substantiated by its positive impact on adaptability, integration, real-time responsiveness, scalability, and fault tolerance. Acknowledging potential challenges, the team is poised to capitalize on the benefits while proactively addressing complexities, learning curve factors, and risks associated with data consistency and routing logic.

Adaptability Benefit: Leveraging an event-driven architecture provides adaptability, empowering the MonitorMe system to seamlessly integrate new features and integrations without causing major disruptions.

