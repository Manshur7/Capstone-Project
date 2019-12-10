# Lumi Monitor - DHT22 Temperature & Humidity Sensor

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
I chose this Lumi project as it would be a way to help young parents monitor the optimum conditions required for the well being of their children & as it would make use of intesting types of sensors.

Sensor used:<br/>
![1](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/dht22Sensor.PNG) <br/>

Concerning software, in order to use ssh connection to my raspberry pi, I had to enable ssh and install xrdp on my raspberry pi before I could get connected. Moreover, I developped the code in python therefore had to install the apropriate libraries for the DHT22 to run in Pyhton.

# Bill of Materials
Raspberry Pi 3 Kit $107 <br/>
DHT22 Temperature & Humidity Sensor $32 <br/>
![1](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/budget.PNG)

Proof of purchase for the required components : <br/>
![1](https://github.com/Manshur7/Capstone-Project/blob/master/Documentation/rpi3.png)
![2](https://github.com/Manshur7/Capstone-Project/blob/master/Documentation/dht22.png) <br/>
Later on, I added a few screws to the purchase to be able to complete the casing for the development platform & Sensor.

# Time Commitment
Even though I stated that it would take me 15 weeks to fully complete this project with its instruction, after having worked on it, I can say that the project can be fresh started and be finished within 3-5 weeks or even less. Acquiring the necessarry parts, PCB printing and PCB soldering plays a major part in completion of the project. Having any relevant experience with any of the aforementioned elements will decrease completion time <br/>
![Schedule](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/schedule.png)

# Mechanical Assembly
The DHT22 is to be connected to a 4 pin header which was soldered on the pcb. In addition, I have soldered an 8 pin header which is directly plugged on to my Raspberry Pi also on the PCB. There is also a 10K resistor which limits the voltage flow to my sensor. This is done to avoid burning my sensor as it is recommended to supply a voltage of 3.3v but mostly as a measure of security <br/>
After designing my case, which included both a 3D printed bottom(Done at the Idea Lab):<br/>
![case1](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/case1.PNG)<br/>
And an acrylic top(Done at the Prototype Lab):<br/>
![case](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/case2.PNG)<br/>
I had to use 2 screws to hold the broadcom development platform in place and on top of these two screws,I mounted the top layer of acrylic which would then cover the RPI and part of the PCB.

# PCB Soldering
For designing the printed circuit board, I have made use of the software Fritzing as it is a user friendly software to help design and print my pcb. The printed pcb required Gerber files which the printing machine will recognize. <br/>
![Pcb Design](https://github.com/Manshur7/Capstone-Project/blob/master/Electronics/pcb1.PNG)

Please make sure to follow the soldering instructions and safety before soldering your pcb. Remember to wear the safety glass. <br/>
This is how my PCB looks after soldering: <br/>
![frontpcb](https://github.com/Manshur7/Capstone-Project/blob/master/Electronics/pcb3.png)
![backpcb](https://github.com/Manshur7/Capstone-Project/blob/master/Electronics/pcb2.png)

# Power Up
I had a few issues setting up the Raspberry Pi to work with my sensor properly. However, after some troubleshooting I was able to get rid of a connection issue which solved the problem as well as make appropriate use of VNC. If any issues occur while trying to use VNC, here is a script that might help you achieve completion faster:
```
Initially, you will require a keyboard, mouse, and monitor to configure the Pi. This will only be needed once.
You will also require an internet connection, either wired, or via wireless.

Set up the Pi as usual, and boot into the Raspbian operating system.
Next, open a terminal window on the Pi.

The first step that should always be done when configuring software packages is to make sure that the installed versions are up to date.
The two commands are:

        sudo apt-get update
        sudo apt-get upgrade

The first of those commands will update the Rapsberry Pi's list of what packages are currently available for download.
The second command then upgrades all installed software packages to the latest version. If you have not done this before, this could take a while to complete.

Next, install the VNC srver with the command:

        sudo apt-get install tightvncserver

This will do two things. First, it will uninstall the realVNC server that is installed by default in Raspbian. Then the tightVNC server will be installed in its place.  RealVNC does not work with the RDP package that will be needed later, which is why it needs to be replaced.

Finally, install the RDP package in the Raspberry Pi with the command:

        sudo apt-get install xrdp

At this point, all the software configuration is set up. The only remaining detail is to locate the IP address that the Raspberry Pi will assign itself when the ethernet port is connected to another computer. This IP address will be in the range 169.254.1.0 to 169.254.254.255 and will be different for each Raspberry Pi, but since it is partially based on the MAC address of the Raspberry Pi, once chosen, the number is unlikely to ever change.

If your Raspberry Pi is connected to a wired network, unplug the ethernet cable from the Raspberry Pi. Connect an ethernet cable from the Raspberry Pi to the USB to Ethernet adaptor, and then plug the USB end of the adaptor into a USB port on a computer running Windows. Next, type this command into the terminal window on the Raspberry Pi:

        ifconfig eth0

This command will return the port information and some statistics about the wired ethernet port on the Raspberry Pi. You will be looking for a line that reads:
        inet 169.254.xx.xx netmask 255.255.0.0  broadcast 169.254.255.255
It may take a few moments for the configuration to complete, so if the line is not present, just repeat the ifconfig command until it is.

The important number is the first one. This is the IP address the Raspberry Pi has picked for itself. The xx represents two numbers in the range of 0 to 254.
It's probably a good idea to write this number down somewhere as you will need to connect a monitor/keyboard/mouse to the computer again to find it if you forget it.

To test the system, on the Windows computer, go to start->accessories->Remote Desktop Connection
It will ask for the IP number to connect to. Type in the IP number you discovered above.
You should get a window opening asking for the username and password to log in to the Raspberry Pi. The username is "pi' and unless you changed it, the password is "raspberry". If you changed the password at any point, use the password you selected instead.

This should get you to a full window with a copy of the Raspberry Pi desktop on it. When you have this, shut down the Raspberry Pi and disconnect the monitor, keyboard, and mouse. Then start the Raspberry Pi back up again.  Once the Raspberry Pi has finished booting, you should be able to use RDP to connect to the Raspberry Pi with the same IP address as before.
```
Here is my code for pulling readings from the sensor and displaying them:<br/>
``` 
#Imports for sensor & Delay
import Adafruit_DHT
from time import sleep

#Assigning pin number and sensor type
DHT_SENSOR = Adafruit_DHT.DHT22
DHT_PIN = 4

#Main
print("		Starting Temperature & Humidity Sensing...")
print("Pulling Readings every 3 seconds")
while True:
    #3 seconds delay in between getting readings
    sleep(3)
    humidity, temperature = Adafruit_DHT.read_retry(DHT_SENSOR, DHT_PIN)

    if humidity is not None and temperature is not None:
        print("Temp={0:0.1f}*C  Humidity={1:0.1f}%".format(temperature, humidity))
    else:
        print("Failed to retrieve data from Sensor")

```
And this is the result of the working code:<br/>
![power up result](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/demo.PNG)


# Unit Testing
To securely test whether the sensor is working appropriately, here is a checklist:<br/>
1.3.3v is connected to VCC on the Raspberry Pi and pin 1 of the DHT22 <br/>
2.GND is connected to pin 4 of the DHT22 and pin 7 of the Raspberry Pi<br/>
3.Data Line is connected to pin 2 of the DHT22 and pin 6 of the Raspberry Pi<br/>
4.Make sure there is a 10K Ohm resistor in between pin 2(Data Line) & pin 1(Power) of the DHT22 <br/>
![individual test](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/breadboard.PNG)<br/>
Below is an example of the first run of the circuit connected in this fashion and the direct code:<br/>
![test run](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/output.PNG)

# Production Testing
This section cover the whole of the project wrapped up.
As you can see on the picture below this is what the final compact case will look like:<br/>
![case](https://github.com/Manshur7/Capstone-Project/blob/master/image%20uploads/prod.PNG)
<br/>
However, If the same project is being manufactured in a larger quantity, soldering could be done through machine intervention to speed up the process. Also, a mass testing of the project can be done by connecting every single one to Wi-Fi, and connecting to them through remote desktop connection.
