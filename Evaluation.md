# Evaluation

## Evaluation methodology: Overall System

### During the development of the project

General performance evaluation of the system:
I want to detect if a break-in occur within 1 second, in order to rapidly detect intrusions without tolerating more than 10 second of delay. I want also to know wich hotspot has been violated.

I will use the following metrics to evaluate the performance of the system:

1. Break-in is dectected within 1 s
2. The hotspot is correctly identified

### When the first complete version of the system will be ready for use

I want to detect if a break-in occur within 1 second, in order to detect intrusions without tolerating more than 10 seconds of delay. We want also to know wich hotspot has been violated, notifying the user within 10 seconds.

1. Break-in is dectected within 1 s
2. The hotspot is correctly identified
3. The notification to the user arrives within 10 seconds.

## Evaluation methodology: Individual Components

I wish to evaluate the power consumption of MCUs, not attached to any power cord. There is an obvious tradeoff between the duty cycle of MCUs, impacting on the accuracy of the salarm ystem, and the duration of the battery. I assumed a time of observation of few months, corresponding to a season. A use case can be in fact a seasonal installation of the system.

+ Power supply of LoRa gateway is provided by a power cord, hence there are no specific constraints on power consumption.
+ MCUs at hotspots: I wish to obtain a battery life equal to the total period of monitoring.

## Network Technologies Performances

+ Latency (s)
+ Throughput (bit/s)

## Algorithms Performances

### Intrusion Detection Algorithm

1. Alarm Activation: check if all fixtures are properly closed

Manual activation:
+ Front door button MCU signal to the LoRa gateway

Remote activation:
+ Cloud signal to the LoRa gateway

+ One request from the LoRa gateway to each MCU
+ One reply from each MCUs (ACK or ERROR)
+ Front door screen and notification feedback (ACK or ERROR) to the user

2. Detection: check if the Hall sensor recognizes any movement 

+ Alert from MCU to the LoRa gateway in case of break-in detection
+ Notification from the cloud to the user

3. Alarm Deactivation: deactivate the alarm system

Manual deactivation (from inside):
+ After providing a password thorugh mobile, front door MCU sends signal to the LoRa gateway

Remote deactivation:
+ Command from user to cloud and from cloud to LoRa gateway

+ Stop signal from LoRa gateway to each MCU
+ Sleeping mode for each MCU

I will evaluate the number of messages sent by the protocol and the time needed to complete the algorithm.
The complexity will change depending on the number of nodes.

### Alarm Algorithm

    def automated_alarm(movement_threshold):

        position = get_position() // From Hall effect sensor
    
        if (position > movement_threshold):
            start_alarm() // Open signal to buzzer
            send_notification() // Send notification to the client through the LoRa gateway
        
        while (not authenticated_stop_signal):
            keep_alarm_on() // Keep signal to buzzer
        
        close()  // Close signal to buzzer

The algorithm perfomance mainly depends on the capacity of the network and the responsivness of the Hall effect sensor.

### Management of the Alarm Algorithm: Alarm Activation and Deactivation

Performances depend on the latency between the cloud, the LoRa gateway and the MCUs.

### Monitoring of the Alarm Algorithm

From the hotspot MCUs, check periodically the state and send a message to the cloud in case of intrusion.
Performances depend on the latency between the cloud, the LoRa gateway and the MCUs.

## Response Time Performances

The response time depends on the distance between the MCUs, so it depends on the topology of the alarm system.
