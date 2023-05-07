# Problem
Today security of interior spaces, in particular houses, is an important security problem to address. Stats reveal that the 66% of burglaries (around 2.5 million each year) are home break-ins. On average, they last less than 10 minutes, so it is important to provide some guarantees in the design of a security system. Although it makes sense to focus on home security, it is easy to understand that a home security system can be easily adapted to other contexts, especially for the protection of generic buildings. 

As detected by CNA, in 2021 the number of reported home thefts in Italy was over 182 thousands, so almost 500 per day, more than 20 per hour, one every 3 minutes. However, there are few Italian families protecting their houses.  Only two out of three possess a security door, less than one third mounted door and window guards, the 30% of families is using security cameras and finally only one third possess an alarm system.

Another important challenge is to provide security to buildings in some contexts of isolation and lack of electrical power.

# Proposed solution
My proposed solution consists of an interface through which it is possible to monitor the state of fixtures of a designed building, ideally a house. The user is rapidly notified in case of break-in detection: the notification includes the location and a timestamp. Obiouvsly all information must be provided according to determined time bound contraints. The movement of a door or a window is detected through an Hall effect sensor combined with a round magnet fixed to the mobile component. The detection will trigger an alarm, which consists of an activated buzzer and a blinking LED, as well as the sending of a notification to the user. I also provide an activation/deactivation button, which must be placed inside the protected building, in order to manually start or stop the alarm system. The alarm system can also be activated or stopped using a mobile.

# Use cases 
My system allows to do the following tasks:
* Manual activation and deactivation of alarm system through button
* Remote activation and deactivation of alarm system through mobile interaction
* Intrusion detection, with timestamp and location
* Automated alarm propagation

# User requirements
* Detect door/window movement: how? Accuracy? FP/FN?
* Proximity: few millimeters
* Promptly: at most in 3 seconds
* Alarm system: actuators
* Events: movement (change of position), so LoRa is a suitable technology
* Works for 1 year on battery
