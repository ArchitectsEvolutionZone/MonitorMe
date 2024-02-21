# MonitorMe infrastructure 

![infrastructure](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/infrastructure.png)

As a hospital that starts using the MonitorMe system, StayHealthy, Inc will provide support for setting up the infrastructure required for a smooth user experience both for patients and medical professionals as well. 

The recommendation is to have the vital sign montioring devices ready in each hospital room, so each time a new patient is registered, devices are at hand and can be connected on the patient. This will help get the patient's vital signs on the Consolidate Monitoring Screen as soon as possible. 

The MonitorMe support team will install Device Gateways in each room, which will pick-up data transmited for the vital sign monitoring devices and forward (over wire) to the Consolidated Monitoring Screen (CMS) and the On-Premise Monitor Me server. 

The On-Premise server will then store and analyze the information, it will communicate with the Web and Mobile apps by Wireless Local Area Network (WLAN) 

The On-Premise MonitorMe server, will host 
* the data storage
* the services required to deliver alerts on the (CSM) and Mobile App
* web server for the Website and Mobile App (backend for the Mobile App)

## MonitorMe infrastructure part delivered by StayHealty,Inc 
- The vital sign devices can be provided by StayHealty, Inc or a set of specifications or vendors can be provided
- Device Gateway
- Consolidated Monitoring Screens
- Server hardware

## Constraints on the hospital 
The hospital's administrative team will need to provide 
- posibility to setup a Wireless Local Area Network
- wire infrastructure accross the hospital's premise

## Non-functional requirements 
- Extensibility. The MonitorMe system is capable of integrating with vital sign monitoring devices that communicate over Bluetooth LE. The Device Gatweay enables easy integration of other type of protocols, being able to transform the information to the format used by MonitorMe system.
- Security. By using strict communication channels, as well as wired communication and secured Wireless Networks, we can limit the the interaction that MonitorMe has with other apps.
- Fast data transder. By having wired communication to the CMS and On-Premise Server, data is transfered fast and reliably. 

## Relevant Architecture Decision Records 
- [Multiple medical devices in communication with the Device Gateway](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/3.ADR/ADR002.md)
- [Device Gateway for data collection and transmission](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/3.ADR/ADR006.md) 
- [Wired communication from Device Gateway to CMS](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/3.ADR/ADR001.md) 
- [Wired communication from Device Gateway to On-Premise Server](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/3.ADR/ADR003.md)
