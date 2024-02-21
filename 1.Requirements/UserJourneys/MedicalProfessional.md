# Medical Professional Role

MonitorMe System is there to support medical professionals in providing the best care for their patients; by being able to monitor patient's vitals signs and react fast when problems arise. Medical professionals are the target audience for this system. 
We've illustrated bellow 3 scenarios where a Medical Professional interacts with MonitorMe system and identified the [use cases](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/1.Requirements/UserJourneys/MedicalProfessional.md#use-cases) that derive from these interactions.

# Medical Professional's Journeys

## Registering patients
![RegisterPatient](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/UserJourneys/registerPatients.png)

## Receiving alerts
![ReceiveAlers](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/UserJourneys/alertsJourney.png)

## Generating vital sign snapshots
![Medical professional](https://github.com/ArchitectsEvolutionZone/MonitorMe/blob/main/resources/UserJourneys/snapshotJourney.png)

# Use cases 
- Register profile for patient in the MonitorMe system. Relevat information to collect: Name, Social Security Number, Status (hospitalized/discharged) 
- Assign patient to a hospital room and assign medical personal that will provide medical care during his stay 
- Link vital sign monitoring devices to patient profile
- MonitorMe system reads data from medical devices 
- Display vital signs on the CMS
- Authenticate medical professional
- Send alerts to apropriate CMS and medical professionals, when patient vital sign is out of the norm
- Generate vital sign snapshot
- Upload vital sign snapshot to MyMedicalData

Out of current scope 
- MonitorMe can send alerts to the Hospital Adminsitrator when one of the monitoring devices is not sending data 


