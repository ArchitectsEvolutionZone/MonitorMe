# Context

![infrastructure](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/C4/Context%20Diagram.jpg)

# Containers

![infrastructure](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/C4/Containers%20Diagram.jpg)

# Components

### Processing vital sign device data 

The Device Gateway has several Device processors, specific to vital sign monitoring devices. This is an extensibility point of the architecture, in case other vital sign devices need to be supported. We can add new Device processors that will take the data transmitted by the new monitoring device, convert it to our preferred format (if it’s the case) and then publish the message over the Event Messaging System. 

The Event Messaging system will distribute the message over several dedicated queues, each vital sign data has its dedicated distribution channels. 
The consumers that attach to the Event Messaging System, will have specific responsibilities. On one hand, these messages are persisted by the Monitoring Data module, residing in the WebApi container. On another hand, the messages are consumed by the Data Analysis Module in order to determine if there is an alert to be published. We plan on caching the other vital signs for a patient in the Data Analysis Module, so the decision of alerting can be made as fast as possible. 

![infrastructure](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/C4/Components%20Diagram.jpg)
