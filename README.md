# Part 1: Setting Up Your Computer
| Name| Type |  
|-----|------|
| ESP8266 (NodeMCU) | NodeMCU ESP8266 WiFi Development Board (CP2102 or CH340)| 
| Laser Diode Module | 5V Laser Diode Module (KY--008)| 
| LDR Sensor Module | Photoresistor LDR Light Sensor Module (KY-018)| 
| Mini Breadboard | 170 Point Mini Solderless Breadboard. 
| Jumper Wires | Male-to-Male (M2M) Breadboard Jumper Wires. Get a multi-colored pack of 20 or more.
| Micro-USB Cable | Micro-USB Data and Power Cable. Make sure this is a data cable (for programming)

# Part 2: Setting Up Your Computer
Before you can program the ESP8266, you need to set up the free Arduino IDE software.

Download Arduino IDE: Go to the official Arduino Software website and download the latest version for your operating system (Windows, Mac, etc.). Install it.

Add ESP8266 Board Manager:
Open the Arduino IDE.
Go to File > Preferences.
In the "Additional Boards Manager URLs" field, paste this exact URL:
```
http://arduino.esp8266.com/stable/package_esp8266com_index.json
```
Click OK.

Install ESP8266 Boards:

Go to Tools > Board > Boards Manager....

In the search box, type esp8266.

The "esp8266 by ESP8266 Community" package will appear. Click the Install button.

Once it's finished, click Close.

Select Your Board:

Go to Tools > Board and scroll down to the "ESP8266 Boards" section.

Select NodeMCU 1.0 (ESP-12E Module).

Your software is now ready!

# Part 3: Assemble the Hardware
Carefully connect your components on the breadboard using jumper wires as shown in the diagram and instructions below.

Circuit Diagram:

Wiring Instructions:

Step 1: Place the ESP8266: Gently push the ESP8266 into the breadboard, straddling the central divider.

Step 2: Connect the LDR Sensor:

VCC pin on LDR module -> 3V3 pin on ESP8266.

GND pin on LDR module -> GND pin on ESP8266.

A0 pin on LDR module -> A0 pin on ESP8266.

Step 3: Connect the Laser Module:

VCC or + pin on laser -> D6 pin on ESP8266.

GND or - pin on laser -> GND pin on ESP8266 (you can use the other GND pin).

Double-check all your connections. Your hardware is now assembled!

# Part 4: Configure and Upload the Code
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

In the Arduino IDE, go to Tools > Port and select the correct COM port.

Click the Upload button (the arrow pointing to the right).

# Part 5: Calibrate and Run!
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
