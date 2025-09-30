# Iot-
Burglar Alert system


Complete Guide: DIY Laser Security System
This guide will walk you through every step to build your WhatsApp-enabled laser tripwire alarm.

Part 1: What to Buy (The Shopping List)
You'll need a few common electronics components. You can find these at local electronics hobby shops in Tirupati or order them easily from online stores like Amazon.in, Robu.in, or ElectronicsComp.com.

Component

Image

Description & Why You Need It

1. ESP8266 (NodeMCU)



This is the brain of your project. It's a small computer with built-in Wi-Fi that will run your code. Make sure you get the "NodeMCU" version as it's the easiest to use on a breadboard.

2. Laser Diode Module



This creates the laser beam. A simple 5V red dot laser module is perfect. It usually has two or three pins.

3. LDR Sensor Module



This is the light sensor that detects the laser beam. Get a module, not just the raw LDR component. The module is easier to wire and has a built-in sensitivity adjustment.

4. Breadboard



This lets you connect all the components without any soldering. A standard "400-point" or "830-point" breadboard is ideal.

5. Jumper Wires



These are the wires you'll use to connect the components on the breadboard. Get a pack of "male-to-male" jumper wires.

6. Micro-USB Cable



You need this to connect the ESP8266 to your computer to upload the code and to power the device later. Make sure it's a data cable, not just a charging cable.

Part 2: Setting Up Your Computer
Before you can program the ESP8266, you need to set up the free Arduino IDE software.

Download Arduino IDE: Go to the official Arduino Software website and download the latest version for your operating system (Windows, Mac, etc.). Install it.

Add ESP8266 Board Manager:

Open the Arduino IDE.

Go to File > Preferences.

In the "Additional Boards Manager URLs" field, paste this exact URL:
http://arduino.esp8266.com/stable/package_esp8266com_index.json

Click OK.

Install ESP8266 Boards:

Go to Tools > Board > Boards Manager....

In the search box, type esp8266.

The "esp8266 by ESP8266 Community" package will appear. Click the Install button. This will take a few minutes.

Once it's finished, click Close.

Select Your Board:

Go to Tools > Board and scroll down to the "ESP8266 Boards" section.

Select NodeMCU 1.0 (ESP-12E Module).

Your software is now ready!

Part 3: Assemble the Hardware
Carefully connect your components on the breadboard using jumper wires as shown in the diagram and instructions below.

Step 1: Place the ESP8266: Gently push the ESP8266 into the breadboard, straddling the central divider.

Step 2: Connect the LDR Sensor:

VCC pin on LDR module -> 3V3 pin on ESP8266.

GND pin on LDR module -> GND pin on ESP8266.

A0 pin on LDR module -> A0 pin on ESP8266.

Step 3: Connect the Laser Module:

VCC or + pin on laser -> D6 pin on ESP8266.

GND or - pin on laser -> GND pin on ESP8266 (you can use the other GND pin).

Double-check all your connections. Your hardware is now assembled!

Part 4: Configure and Upload the Code
This is where you tell the code your specific details.

Get WhatsApp API Key:

Go to the CallMeBot website.

Follow their instructions. You will add their phone number to your contacts and send a specific message to it.

The bot will reply with your unique API Key. Copy this key.

Edit the Code:

Open the LaserSecuritySystem.ino file in the Arduino IDE.

Scroll down to the USER CONFIGURATION section.

Change these three lines:

const char* ssid = "YOUR_HOSTEL_WIFI_SSID";
String phoneNumber = "+910000000000";
String apikey = "YOUR_CALLMEBOT_APIKEY";

Replace YOUR_HOSTEL_WIFI_SSID with the exact name of your hostel's Wi-Fi network.

Replace +910000000000 with your WhatsApp phone number, including the +91 country code.

Replace YOUR_CALLMEBOT_APIKEY with the key you just got.

Upload:

Connect the ESP8266 to your computer with the micro-USB cable.

In the Arduino IDE, go to Tools > Port and select the correct COM port (it will usually be the only one that appears when you plug the board in).

Click the Upload button (the arrow pointing to the right). The IDE will compile and upload the code.

Part 5: Calibrate and Run!
This is the final and most important step to make the system accurate.

Open Serial Monitor: After uploading, keep the board connected and go to Tools > Serial Monitor. In the bottom-right of the window, set the speed to 115200 baud.

Get IP Address: The ESP8266 will connect to the Wi-Fi and print its IP Address. It will look something like 192.168.43.125. Write this down.

Calibrate the Sensor:

Uncomment these two lines in the loop() function by removing the //:

// Serial.print("LDR Value: "); // Uncomment for calibration
// Serial.println(ldrValue);     // Uncomment for calibration

Re-upload the code.

Now, open the Serial Monitor again. It will continuously print the LDR sensor's reading.

Reading 1: Aim the laser so the dot is directly on the LDR sensor. Write down the number you see (e.g., LDR Value: 85).

Reading 2: Block the laser beam with your hand. The number will jump up. Write this new, higher number down (e.g., LDR Value: 850).

Set the Threshold: Choose a number that is in the middle of your two readings. In our example, a good threshold would be 500.

Update this line in your code with your calculated value:

int threshold = 500; // Change 500 to your value

Comment out the two print lines again and re-upload the code one last time.

Deploy and Use:

Disconnect the ESP8266 from your computer. You can now power it with any USB phone charger.

Place the laser module and the sensor module across a doorway or the area you want to protect, ensuring the laser hits the sensor.

On your phone (connected to the same hostel Wi-Fi), open a browser and type in the IP Address you wrote down.

You will see the control panel to ARM and DISARM the system.

You are all done! When the system is armed and someone breaks the beam, you will get a WhatsApp message.


```
Complete Guide: DIY Laser Security System
This guide will walk you through every step to build your WhatsApp-enabled laser tripwire alarm.

Part 1: What to Buy (The Shopping List)
You'll need a few common electronics components. You can find these at local electronics hobby shops in Tirupati or order them easily from online stores like Amazon.in, Robu.in, or ElectronicsComp.com.

Component

Full Product Name / What to Search For

Image

1. ESP8266 (NodeMCU)

NodeMCU ESP8266 WiFi Development Board (CP2102 or CH340). This is the brain of your project. It has built-in Wi-Fi. The "NodeMCU" version is essential as it fits perfectly on a breadboard.



2. Laser Diode Module

5V Laser Diode Module (KY-008). You are looking for a simple red dot laser that operates at 5 volts. Searching for the model number "KY-008" will give you the exact module.



3. LDR Sensor Module

Photoresistor LDR Light Sensor Module (KY-018). This is a Light Dependent Resistor. Be sure to buy the module, which includes extra components, not just the raw sensor. Searching "KY-018" will find it.



4. Breadboard

400 Point Solderless Breadboard. This lets you connect everything without soldering. A 400-point breadboard is the perfect size for this project.



5. Jumper Wires

Male-to-Male (M2M) Breadboard Jumper Wires. Get a multi-colored pack of 20 or more. The "male" ends have pins that plug into the breadboard and modules.



6. Micro-USB Cable

Micro-USB Data and Power Cable. It is very important that this is a data cable (sometimes called a sync cable), not a charge-only cable. It's the same type used for many older Android phones.



Part 2: Setting Up Your Computer
Before you can program the ESP8266, you need to set up the free Arduino IDE software.

Download Arduino IDE: Go to the official Arduino Software website and download the latest version for your operating system (Windows, Mac, etc.). Install it.

Add ESP8266 Board Manager:

Open the Arduino IDE.

Go to File > Preferences.

In the "Additional Boards Manager URLs" field, paste this exact URL:
http://arduino.esp8266.com/stable/package_esp8266com_index.json

Click OK.

Install ESP8266 Boards:

Go to Tools > Board > Boards Manager....

In the search box, type esp8266.

The "esp8266 by ESP8266 Community" package will appear. Click the Install button. This will take a few minutes.

Once it's finished, click Close.

Select Your Board:

Go to Tools > Board and scroll down to the "ESP8266 Boards" section.

Select NodeMCU 1.0 (ESP-12E Module).

Your software is now ready!

Part 3: Assemble the Hardware
Carefully connect your components on the breadboard using jumper wires as shown in the diagram and instructions below.

Step 1: Place the ESP8266: Gently push the ESP8266 into the breadboard, straddling the central divider.

Step 2: Connect the LDR Sensor:

VCC pin on LDR module -> 3V3 pin on ESP8266.

GND pin on LDR module -> GND pin on ESP8266.

A0 pin on LDR module -> A0 pin on ESP8266.

Step 3: Connect the Laser Module:

VCC or + pin on laser -> D6 pin on ESP8266.

GND or - pin on laser -> GND pin on ESP8266 (you can use the other GND pin).

Double-check all your connections. Your hardware is now assembled!

Part 4: Configure and Upload the Code
This is where you tell the code your specific details.

Get WhatsApp API Key:

Go to the CallMeBot website.

Follow their instructions. You will add their phone number to your contacts and send a specific message to it.

The bot will reply with your unique API Key. Copy this key.

Edit the Code:

Open the LaserSecuritySystem.ino file in the Arduino IDE.

Scroll down to the USER CONFIGURATION section.

Change these three lines:

const char* ssid = "YOUR_HOSTEL_WIFI_SSID";
String phoneNumber = "+910000000000";
String apikey = "YOUR_CALLMEBOT_APIKEY";

Replace YOUR_HOSTEL_WIFI_SSID with the exact name of your hostel's Wi-Fi network.

Replace +910000000000 with your WhatsApp phone number, including the +91 country code.

Replace YOUR_CALLMEBOT_APIKEY with the key you just got.

Upload:

Connect the ESP8266 to your computer with the micro-USB cable.

In the Arduino IDE, go to Tools > Port and select the correct COM port (it will usually be the only one that appears when you plug the board in).

Click the Upload button (the arrow pointing to the right). The IDE will compile and upload the code.

Part 5: Calibrate and Run!
This is the final and most important step to make the system accurate.

Open Serial Monitor: After uploading, keep the board connected and go to Tools > Serial Monitor. In the bottom-right of the window, set the speed to 115200 baud.

Get IP Address: The ESP8266 will connect to the Wi-Fi and print its IP Address. It will look something like 192.168.43.125. Write this down.

Calibrate the Sensor:

Uncomment these two lines in the loop() function by removing the //:

// Serial.print("LDR Value: "); // Uncomment for calibration
// Serial.println(ldrValue);     // Uncomment for calibration

Re-upload the code.

Now, open the Serial Monitor again. It will continuously print the LDR sensor's reading.

Reading 1: Aim the laser so the dot is directly on the LDR sensor. Write down the number you see (e.g., LDR Value: 85).

Reading 2: Block the laser beam with your hand. The number will jump up. Write this new, higher number down (e.g., LDR Value: 850).

Set the Threshold: Choose a number that is in the middle of your two readings. In our example, a good threshold would be 500.

Update this line in your code with your calculated value:

int threshold = 500; // Change 500 to your value

Comment out the two print lines again and re-upload the code one last time.

Deploy and Use:

Disconnect the ESP8266 from your computer. You can now power it with any USB phone charger.

Place the laser module and the sensor module across a doorway or the area you want to protect, ensuring the laser hits the sensor.

On your phone (connected to the same hostel Wi-Fi), open a browser and type in the IP Address you wrote down.

You can now see the control panel to ARM and DISARM the system.

You are all done! When the system is armed and someone breaks the beam, you will get a WhatsApp message.
```
