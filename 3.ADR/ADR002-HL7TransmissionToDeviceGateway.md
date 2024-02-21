# Use of Multiple Medical Devices for Direct Data Transmission to Gateway, using HL7

## Context
The current hospital environment relies on larger, centralized medical devices for patient data collection and transmission. 
However, this approach has limitations in terms of mobility, scalability, and adaptability to varying patient needs. 
The emergence of smaller, portable medical devices with built-in data transmission capabilities has opened up the 
possibility of decentralizing data collection and transmission processes. 
This shift could potentially improve patient care, increase efficiency, and enable more dynamic patient monitoring.

## Status
Proposed

## Decision
It is proposed to adopt the use of multiple smaller HL7 standard medical devices to send data directly to the Gateway,
in order to achieve the following benefits:
   * Interoperability: The HL7 standard ensures that medical devices from different vendors can communicate and share data seamlessly, reducing vendor lock-in and allowing for greater flexibility in device     selection. 
   * Data Standardization: HL7 provides a standardized format for data exchange, making it easier to integrate new devices and systems into the hospital's existing infrastructure.
   * Streamlined Data Management: HL7 facilitates the exchange of structured, standardized data, reducing the need for manual data entry and improving data quality.
   * Regulatory Compliance: HL7 is widely recognized and adopted in the healthcare industry, helping hospitals to comply with regulatory requirements for data exchange and interoperability.
    
## Consequences
In order to be in regulatory compliance, improve data quality and enhance interoperability, using an established protocol like HL7 
to facilitate data transmission between device and gateway would be ideal, would lead to lower costs in the long run 
due to lower implementation costs for standard protocols, which also permits a wider range of sensors and medical devices to be integrated.
This same protocol would be used going forward to any and all transfer of medical data.
