# Core requirements
Our analysis on the client's requirements concludes that these are the essential features of the system
- MonitorMe system receives data from medical devices and does not fail when one of the medical devices is down 
- The Consolidated Monitoring Screen is updated with patient's vital signs in under 1 second 
- Medical professional receive alerts when patient's vital signs are out of norm 

# Project Constraints 
- OnPremise infrastructure
- Fast data transfer:  1s data delay between communication points is acceptable 
- Integration with MyMedicalData - upload snapshot functionality
- Changing requirements 

# Architecture characteristics
Based on the core requirements, the following architecture characteristics were identified 
- Responsivnes. Health data should reach the Consolidated Monitoring Screen in less than 1 second. 
- Fault tolerance. The system is required to work even when some of it's devices are down, continuing to process information and deliver data for medical professionals. As further development, we propose to alert the hospital administrator when a device is detected as being faulty (the system din't receive data from it as expected).
- Performance. The component of the system responsible for analyzing vital sign data plays a pivotal role in responding promptly. It is critical for swift and timely action, facilitating instant alerts to medical professionals.
- Accuracy. Vital sign data that is analyzed and recorded must be as accurate as possible since human lives are at stake. The monitoring device types and supported protocols need to be analyzed and established so we can atest to the quality of the data that is sent into the system. 
- 