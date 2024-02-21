# Device Gateway Wired Communication with On-Premise Server "MonitorMe"

## Context
The on-premise server "MonitorMe" serves as a vital component in the hospital's data management infrastructure. 
It's responsible for receiving, storing, and updating patient medical data from various sources, including the devices mentioned earlier. 
Given the critical nature of this data and the need for rapid access, 
ensuring a robust and reliable communication method between the devices and the server is paramount.

## Status
Proposed

## Decision
The decision is to implement a wired communication protocol between the Device Gateway and the on-premise server "MonitorMe."
Reasons for this choice are:
   * Reliability: Wired connections generally offer better reliability and consistency compared to wireless alternatives, reducing the risk of data loss or transmission errors.
   * Security: Wired communication is inherently more secure as it's not subject to the same vulnerabilities as wireless transmissions, such as interception or interference.
   * Bandwidth: Wired connections typically offer higher bandwidth, allowing for faster data transfer, essential for real-time patient monitoring.
   * Stability: Wired connections are less prone to environmental factors that can affect wireless signals, ensuring a stable and consistent connection.

## Consequences
Using a wired communication protocol brings plenty of pros and also some cons, as we minimize the risk of data corruption and loss, increasing security due to physical wires, 
and also being a fast and reliable way to access the on-premise server data quickly which enbles faster decision making. The infrastructure setup cost is to be mentioned, as
implementing this would require additional investment in cabling, switches and other related equipment, as well as installation and maintenance.
