# Smart Car Parking System using 8051 Microcontroller
## Overview
The Smart Car Parking System is designed to provide an efficient, reliable, and automated solution to modern parking challenges. It is built using an 8051 microcontroller, IR sensors, servo motors, and an LCD display.

The 8051 microcontroller acts as the brain of the system, processing signals from the IR sensors and controlling the servo motors as well as the LCD. The IR sensors are responsible for detecting the presence of vehicles at the entrance and exit points, while the servo motors automatically open and close the gates based on these signals. The LCD display provides real-time updates of the available parking slots to drivers.

By automating the process of detecting vehicles, managing gates, and updating slot counts, this system ensures better space utilization, reduced congestion, and enhanced driver convenience compared to traditional parking methods.

## Working:

### Startup:

- When the system is powered on, the total number of available slots is displayed on the LCD.

### Vehicle Entry:

- When a car arrives at the entrance, the IR sensor detects its presence.

- The microcontroller checks whether any slots are available.

- If a slot is free, the 8051 triggers the servo motor to rotate 90° and open the entrance gate.

- The slot count is decremented by one and the LCD is updated with the new availability.

- After a short delay (about 5 seconds), the gate automatically closes.

### Vehicle Exit:

- When a car moves to the exit gate, the IR sensor at the exit detects it.

- The microcontroller triggers the exit gate’s servo motor to open.

- Once the car leaves, the slot count is incremented by one and the LCD is updated.

- The exit gate then closes automatically after a short delay.

### Full Parking Condition:

- If all slots are occupied, the microcontroller prevents the entrance gate from opening, even if the sensor detects a vehicle.

- This avoids unnecessary congestion at the entry point.

### False Trigger Handling:

- If the exit sensor accidentally detects movement when no vehicle is inside, the gate does not open.

- This improves system reliability and avoids errors.

## Advantages:

- Accurate Vehicle Detection: IR sensors ensure reliable detection of vehicles at both entry and exit.

- Automatic Gate Control: Servo motors automate gate operations, removing the need for manual effort.

- Real-Time Updates: Drivers are informed instantly about available slots on the LCD.

- Improved Security: Unauthorized entry is prevented as the system only allows cars when slots are available.

- Optimized Space Utilization: Slot counts are managed efficiently, ensuring maximum use of available space.

- Cost-Effective Solution: Using an 8051 microcontroller keeps the system affordable and easy to maintain.

- User-Friendly: Simple interface and automatic operation make it convenient for drivers.

- Scalability: The system can be expanded for larger parking lots by adding more sensors and displays.

## Code 
  - <a href="https://github.com/HariharanNedunchezhiyan/Car-Parking-System-using-8051-MicroController/blob/main/Code" > Code

## Block Diagram
<img width="628" height="331" alt="image" src="https://github.com/user-attachments/assets/8c749fc4-8ffd-4197-9613-7e80056d091e" />

## Flow Chart
<img width="463" height="573" alt="image" src="https://github.com/user-attachments/assets/3da503ea-5e2e-42bf-a96c-e42219ac4e77" />

## Proteus Simulation Result 

### 1. Initial Stage of the System
At the beginning, when the system is powered on, both the IR sensors (placed at the entrance and exit gates) are in a low state, meaning no vehicles are detected. The two servo motors that control the gates remain in the closed position. On the LCD display, the total number of free slots is shown—in our case, it starts with 10 available slots. This ensures that drivers know the parking status before entering.

<img width="783" height="532" alt="image" src="https://github.com/user-attachments/assets/06a1fb88-bbe7-4e13-a3ce-c29bf66be218" />

### 2. Vehicle at the Entrance Gate
When a car arrives at the entrance of the parking slot, the IR sensor placed near the gate detects its presence. At this moment, the sensor output goes high and sends a signal to the 8051 microcontroller. The microcontroller then commands the entrance servo motor to rotate 90 degrees, which causes the gate to open. This automatic response removes the need for manual gate operation and makes the entry process faster and easier for drivers.   

<img width="795" height="539" alt="image" src="https://github.com/user-attachments/assets/0401a0f6-a3d8-4607-bac6-2ab08a29090a" />

### 3. Updating Slots After Entry
Once the car has entered through the gate, the system provides a 5-second delay to allow the vehicle to pass safely. After this time, the servo motor rotates back to its original position, closing the gate securely. At the same time, the slot counter is decremented by 1, reducing the available count from 10 to 9. This updated slot count is instantly displayed on the LCD screen, keeping the information accurate and real-time for other drivers.

<img width="807" height="553" alt="image" src="https://github.com/user-attachments/assets/0c4c4d7c-6b80-40e1-8e98-b07a0c3dc0de" />

### 4. Vehicle at the Exit Gate
When a car approaches the exit of the parking lot, the IR sensor positioned near the exit detects its movement. Similar to the entrance, the sensor sends a signal to the 8051 microcontroller. The microcontroller responds by activating the exit servo motor, which rotates 90 degrees to open the gate. This ensures that the vehicle can leave the parking space without any manual effort.

<img width="814" height="554" alt="image" src="https://github.com/user-attachments/assets/8b901e5a-ff38-4fd9-8e44-cd2feea2f8e7" />

### 5. Updating Slots After Exit
Once the car leaves the parking area, the gate remains open for about 5 seconds to give the vehicle enough time to pass. After this short delay, the servo motor returns to its initial position, closing the exit gate. At the same time, the microcontroller increments the slot count by 1, as one parking space has now become free. For example, the display will change from 9 to 10 available slots. This updated count is shown immediately on the LCD display.

<img width="824" height="554" alt="image" src="https://github.com/user-attachments/assets/145f6eb9-6228-44fd-be6d-950957437137" />

### 6. Handling a Full Parking Condition
If the parking lot becomes completely full, the system ensures safety and prevents congestion at the entrance. In this case, even if a vehicle arrives and the IR sensor at the entrance detects it, the microcontroller will not activate the servo motor. This means the entrance gate remains closed, and the car cannot enter until a slot becomes free. This feature avoids confusion for drivers and ensures that the parking lot is never overloaded.

<img width="874" height="597" alt="image" src="https://github.com/user-attachments/assets/a5a3b792-3008-4132-8a48-de8affec7495" />

### 7. Preventing False Triggers at the Exit
Sometimes IR sensors can generate false signals due to environmental conditions or accidental movements. To handle this, the system has been programmed carefully. For example, if the IR sensor at the exit gate accidentally detects a signal when there is no car inside the parking area, the exit gate will not open. This prevents unnecessary gate operations, saves power, and makes the system more reliable.

<img width="868" height="588" alt="image" src="https://github.com/user-attachments/assets/5aa0bd3c-c90a-40ae-b54a-af4ef0d7f3e3" />

## Conclution
- In conclusion, our Smart Car Parking System provides a modern, automated, and reliable solution to parking management. Using an 8051 microcontroller, IR sensors, servo motors, and an LCD display, it successfully automates vehicle entry and exit, prevents unauthorized or unnecessary gate operations, and displays real-time slot availability.

- This system not only saves time and reduces congestion but also ensures better safety, space optimization, and user convenience. Its low cost, scalability, and efficiency make it a practical choice for real-world parking environments, from small institutions to large commercial complexes.

