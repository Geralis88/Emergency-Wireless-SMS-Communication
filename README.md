
# Emergency Wireless SMS Communication System

This project uses ESP32 microcontrollers, RYLR998 modules, and LoRa technology to construct an emergency wireless communication system. It is intended to offer reliable, two-way communication in disaster-affected areas when conventional networks, such the internet and cellphone systems, are not accessible.

# Circuit Design and Explanation
The ESP32 microcontroller, the LoRa RYLR998 module, and a regulated power source are all built into the circuit design of this emergency communication system in Figure 5. This makes it a reliable and self-sufficient way to communicate during disasters. The power source starts with a 9V battery connected to a Pololu D24V22F5 step-down voltage regulator. This regulator effectively changes the 9V input to a stable 5V output that the ESP32 needs to work. Furthermore, the ESP32 also gives off 3.3V to power the LoRa module. This makes sure that the power transfer system works smoothly, which lets the circuit work well even when there isn't much power.

Besides that, the ESP32 is the main processor and transmission hub. It allows direct connections to cell phones through Bluetooth and communicates with the LoRa module through UART. The LoRa RYLR998 module also makes long-range data transfer possible, which makes it perfect for staying in touch over long distances where regular infrastructure isn't available. The GPIO 17 on the ESP32 is connected to the RX pin of the LoRa module, and GPIO 16 on the ESP32 is connected to the TX pin of the LoRa module. To make the UART connection, these pins are joined together.

In terms of operation, the system sends messages by first allowing users to send text data via a mobile application, such as the "Serial Bluetooth Terminal," to the ESP32 over Bluetooth. Following this, the ESP32 interprets the message and forwards it to the LoRa module for broadcast via a long-range wireless link. Once received, another LoRa module decodes the data and sends it to its connected ESP32, which subsequently relays the message to the recipient's mobile device over Bluetooth. Importantly, the LoRa communication employs unlicensed sub-GHz frequency channels, such as 868 MHz in Europe or 915 MHz in North America, so assuring compliance with regional legislation. Lastly, the energy efficiency of the system is boosted by the Pololu step-down voltage regulator, which stabilizes the power supply while minimizing energy wastage. Consequently, this structure enables portable and autonomous functioning, making the device a dependable tool in disaster-stricken areas. In conclusion, the design combines energy-efficient components, seamless communication interfaces, and robust long-range capabilities, hence providing a scalable and durable solution for emergency communication demands.

>>>>>>>>>>>>![Circuit Diagram](https://github.com/user-attachments/assets/7e1e1b85-e6ae-40c6-8b71-6ba4b5149de8)
                 
                        Figure 1 Emergency communication circuit diagram.
![Schematic of the circuit](https://github.com/user-attachments/assets/77186294-d396-4b2a-a665-b71667193bad)

                        Figure 2 Schematic of the circuit.
![physical implementation of the circuit](https://github.com/user-attachments/assets/ee26187a-6dc9-4a57-ab20-e6b80b0a2e20)

                                                Figure 3 Physical implementation of the circuit.
Components to realize this project:

-ESP32 Module: Runs code, connects LoRa module via Bluetooth.  
-Breadboard: Builds and organizes the circuit.  
-Voltage Regulator: Converts 9V to 5V for ESP32; ESP32 steps down to 3.3V for LoRa.  
-Battery Holder: Holds and connects the 9V battery.  
-9V Battery: Powers the system.  
-Wire Jumpers: Links components on the breadboard.  
-Cellphone: Sends/receives messages via Bluetooth using an app.  
-GPIO Breakout Board: Organizes ESP32 connections. 

 




# Results
In Mode 0, the system enables message dissemination to all nodes. Node #0 is designated as the principal recipient for the transmission of such messages. The employed message format is 0, message, guaranteeing consistency and effective transmission throughout the network. 

>>>>>>>>![image](https://github.com/user-attachments/assets/9b60b00c-2252-4383-9acf-82e04bfccdad)

          Figure 4 Message sent from Node 3 to Nodes 1 and 2 with the required format (blue words).


>>>>>>>![image](https://github.com/user-attachments/assets/04157fe7-f120-4831-9aef-93f9660bc146)

            Figure 5 Message received from Node 3 in Node 1.

>>>>>>>![image](https://github.com/user-attachments/assets/ba620538-22c0-43fd-b417-589973a99739)

               Figure 6 Message received from Node 3 in Node 2.
In Mode 2, the system is set up for direct communication among designated nodes. Messages are transmitted in format 2, message, where "2" denotes the intended node. For instance, when a message is conveyed from Node 1 to Node 2, it is received precisely at Node 2, validating the system's capacity for effective, direct communication. This mode emphasizes the network's accuracy and dependability in transmitting messages to specified nodes.


>>>>>>>>![image](https://github.com/user-attachments/assets/b3605846-ad6a-4e80-9faa-090e5a3716da)

      Figure 7 Message sent from Node 1 with the required format (blue words).

>>>>>>>>![image](https://github.com/user-attachments/assets/5930a81b-56df-408a-9d51-7153def35818)


              Figure 8 Message received in Node 2 from Node 1.
Mode 1 establishes a direct communication link, primarily aimed at Node 1. Messages dispatched from Node 2 adhere to the format 1, message, and are consistently received, decoded, and transmitted to the device at Node 1. This illustrates the system's capability to guarantee accurate and efficient message transmission to the designated node.


>>>>>>>![image](https://github.com/user-attachments/assets/e5866660-1455-48fe-9baa-719fb0d80495)

        Figure 9 Message sent from Node 2 with the required format (blue words) to Node 1.

>>>>>>>>![image](https://github.com/user-attachments/assets/236605ee-5108-4f49-a737-cb0676466df8)

         Figure 10  Message received in Node 1 from Node 2.
Range distance test of 1.26km:

![image](https://github.com/user-attachments/assets/616954ac-e661-4682-b01b-51589ad89f48)

Range distance test of 687.96m:

![image](https://github.com/user-attachments/assets/d8591808-e88c-4622-afb6-9a8ded22e7b0)

Range distance test of 669.03m:

![image](https://github.com/user-attachments/assets/e760038e-8d79-4062-9565-33245045dc3e)


References:

[1]. R. B. Reese, Microprocessors: From Assembly Language to C Using the PIC18FXX2, 
      Charles River Media, 2005.

[2]. Kai Morich, "Serial Bluetooth Terminal," [Online]. 
      Available: https://play.google.com/store/apps/details?id=de.kai_morich.serial_bluetooth_terminal&hl=en-US. 
     
[3]. Arduino, "Arduino IDE 2.3.2 Simulator," [Online]. Available: https://www.arduino.cc/en/software.  
      
[4]. Circuitstate Electronics, "ESP32-DevKit-V1 Pinout," [Online]. 
      Available: https://circuitstate.com/wp-content/uploads/2022/12/ESP32-DevKit-V1-Pinout-r0.1-CIRCUITSTATE-Electronics.pdf. 

[5]. Reyax Technology, "RYLR998 LoRa Module," [Online]. Available: https://reyax.com/products/rylr998/. 
      
[6]. Draw.io, "Draw.io Diagram Tool," [Online]. Available: https://draw.io. 

[7]. Fritzing, "Fritzing Project Tool," [Online]. Available: https://fritzing.org/. 
       
[8]. Circuit Digest, "Introduction to LoRa and LoRaWAN," [Online]. 
      Available: https://circuitdigest.com/article/introduction-to-lora-and-lorawan-what-is-lora-and-how-does-it-work. 



