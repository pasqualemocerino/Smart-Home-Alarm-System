# Design

## Architecture 
![architecture](link image) <br/>
The core idea of my system is flexibility, both of context of use and of power availability. The system is thought to be used in absence of power supply. This choice is motivated by the burden of adaptation to a specific house and the necessity of cable management in the case of direct power supply. Although it is not applicable to all contexts, this last mentioned solution is undoubtedly feasible in most cases and more durable: I thought about a possible adaptation to that case, but it is not the main focus. The scalability of my system is related to the possibility to monitor an increasing number of buildings.

My architecture can be used to monitor the security of one or more houses (or, more generally, of buildings), typically composed of multiple hotspots (doors or windows), that can be violated by burglars. I assume the possibility to protect also a single hotspot, that can be an independent door that is not part of a building. The architecture is scalable and can be used to control the state of a point of interest, or different places simultaneously.

## High level diagram
![diagram](image link) <br/>
My system is made up of 3 different components:

* Battery-powered MCUs in correspondence of windows and doors
* LoRa router, connected through a power cord, that connects the MCUs in the same area
* Battery-powered MCU mounted on front door, with the activation/deactivation button

## Components
My infrastructure is composed of:
* ESP32 MCU with LoRa support for peer and cloud communication 
* Hall effect sensor
* Round magnet
* Buzzer
* LED
* Button
* Cloud system (AWS) to collect and store data

### ESP32
The ESP32 manages the different sensors and actuators in the infrastructure and exchanges messages with the other microcontrollers and with the cloud. The main technical issue is that devices will be attached to every object of interest and must implement an intensive duty cycle in order to be effective, thus they should be properly battery-powered.
There are two main MCU unities:
* An MCU for each hotspot
* A MCU connected to the activation button, on the outside

### LoRa
LoRa is a physical radio communication protocol, based on spread spectrum modulation techniques derived from chirp spread spectrum (CSS) technology. The protocol is supported by my chosen ESP32 MCUs, allowing a low power and long range communication between microcontrollers in order to accomplish distributed tasks.

### Sensors
#### Hall effect sensors
Hall effect sensors can detect the presence and strength of a magnetic field. Their working principle states that when a current-carrying conductor or semiconductor with current flowing in one direction is introduced perpendicularly to a magnetic field, a voltage can be measured at right angles to the current path.


#### Button
A button is a simply sensor also called pushbutton, tactile button or momentary switch. This basic component is placed on some extrernal location, used to activate and/or deactivate the alarm system. 

### Actuators
#### Buzzer
A buzzer is an audio signaling device, it may be electromechanical or piezoelectric or mechanical type. Its main function is to convert the signal from audio to sound. An electromagnetic buzzer is made with a magnet, solenoid coil, oscillator, housing, vibration diaphragm, and magnet. Once the power supply is given, the oscillator which produces the audio signal current will supply throughout the solenoid coil to generate a magnetic field. Sometimes, the vibration diaphragm will vibrate and generates sound under the magnet and solenoid coil interaction. The frequency range of this ranges from 2 kHz to 4kHz. Mechanical buzzers are subtypes of electromagnetic, so the components used in this type are also similar. But the main difference is that the vibrating buzzer is placed on the outside instead of the inside.

#### LED
I use red light LED diodes for signalling purposes. When an electric current passes through the LED, the electrons recombine with holes emitting light. This is achieved by allowing the current to flow in the forward direction and blocking it in the reverse direction.


### Cloud system
Data are stored on AWS for long term storage. In this way from logs it is also possible to obtain statistics about break-ins in different locations. These data can then be queried by authorized users in order to gain insights about the state of fixtures of their monitored houses.

## Network architecture 
![network](image link) <br/>
The network architecture is focused on checking the actual state of the security system, with a communication between devices based on LoRaWAN and MQTT.

## Algorithms 
### Intrusion detection algorithm
![messages](image link) <br/>
This is the communication scheme between IoT elements, Edge components, and Cloud components, related to the algorithm for the intrusion detection.
