# Lumi Monitor Capstone-Project

### Table of Contents
1.  [Introduction](#Introduction)
2.  [Bill of Materials/Budget](#Bill-of-Materials) 
3.  [Time Commitment](#Time-Commitment)
4.  [Mechanical Assembly](#Mechanical-Assembly)
5.  [PCB/Soldering](#PCB-Soldering)
6.  [Power Up](#Power-Up)
7.  [Unit Testing](#Unit-Testing)
8.  [Production Testing](#Production-Testing)

# Introduction
I chose this Lumi project as it was a way to help young parents monitor the optimum conditions required for the well being of their children & as it would make use of intesting types of sensors.

Sensor used: ![1](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/dht22Sensor.PNG) <br/>

Concerning software, in order to use ssh connection to my raspberry pi, I had to enable ssh and install xrdp on my raspberry pi before I could get connected. Moreover, I developped the code in python therefore had to install the apropriate libraries for the DHT22 to run in Pyhton.

# Bill of Materials
Raspberry Pi 3 Kit $107 <br/>
DHT22 Temperature & Humidity Sensor $32 <br/>
[1](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/budget.PNG)

Proof of purchase for the required components : <br/>
![1](https://github.com/Manshur7/Capstone-Project/blob/master/Documentation/rpi3.png)
![2](https://github.com/Manshur7/Capstone-Project/blob/master/Documentation/dht22.png) <br/>
Later on, I added a few screws to the purchase to be able to complete the casing for the development platform & Sensor.

# Time Commitment
Even though I stated that it would take me 15 weeks to fully complete this project with its instruction, after having worked on it, I can say that the project can be fresh started and be finished within 3-5 weeks or even less. Acquiring the necessarry parts, PCB printing and PCB soldering plays a major part in completion of the project. Having any relevant experience with any of the aforementioned elements will decrease completion time <br/>

# Mechanical Assembly
The DHT22 was to be connected to a 4 pin header which was soldered on the pcb. In addition, I have soldered an 8 pin header which is directly plugged on to my Rpi also on the PCB. There is also a 10K resistor which limits the voltage flow to my sensor. This is done to avoid burning my sensor as it is recommended to supply a voltage of 3.3v but mostly as a measure of security <br/>
After designing my case, which included both a 3D printed bottom and an acrylic top(Done at the Idea Lab & Prototype Lab), I had to use 2 screws to hold the broadcom development platform in place and on top of these two screws,I mounted the top layer of acrylic which would then cover the RPI and part of the PCB.

# PCB Soldering
For designing the printed circuit board, I have made use of the software Fritzing as it is a user friendly software to help design and print my pcb. The printed pcb required Gerber files which the printing machine will recognize. <br/>
![Pcb Design](https://github.com/Manshur7/Capstone-Project/blob/master/Electronics/pcb1.PNG)

Please make sure to follow the soldering instructions and safety before soldering your pcb. Remember to wear the safety glass. <br/>
This is how my PCB looks after soldering: <br/>
![frontpcb](https://github.com/Manshur7/Capstone-Project/blob/master/Electronics/pcb3.png)
![backpcb](https://github.com/Manshur7/Capstone-Project/blob/master/Electronics/pcb2.png)
