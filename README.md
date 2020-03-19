# The Rex Ventilator

## !! Warning everything in this repository is for information purposes only. !!

### Do not build or use this device on any person. This is not medical grade equipment and has a high probability that it could cause significant injury or death. By reading, sharing, implementing, deriving works from, or copying any of this information you assume all liability and absolve liability from the author.

[![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/images/video_thumbnail.jpg)](https://youtu.be/pFnB-vOWQmU "Rex Ventilator")

## Overview

The Coronavirus is projected to overwhelm the capabilities of most hospital systems during the growth and peak of cases requiring mechanical ventilators. Most ventilators are in short supply and it maybe impossible in many countries to get more. As care is rationed many people are projected to die if not given ventilation at an Intensive Care Unit (ICU). The Rex Ventilator is a prototype design to explore low cost - high availability designs to help fill this gap in the system that would support the breathing of a patient who was unable to breath on their own.

As such, the 'Rex' ventilator is designed to be built from off the shelf parts, be constructed quickly, and be broadly servicable by anyone with basic knowledge of electronics and software design. The Rex would be connected to an air supply (provided by a commercial generator), and then be connected to the patient via intubation. This design is inspired from an earlier 'pandemic ventilor' but added updated controls and an improved air bag design. It is a prototype of a solution that would need further development, but could provide a start point for that work.

The design is made up of three elements:
 - The hardware base
 - Air system (tubes and valves)
 - Electronics and Power supply

# Current Status / Limitations
1) The exhaust valve solenoids should be increased in size from 1/4 to 1/2 to allow for greater exhailing flow rate
2) There is currently no pressure sensing on the patient side of the ventilator - additional sensors can be added
3) The reed switches need to be moved manually - would be better if a sliding potentiometer was used to more actively control the range
4) No emergency alert is created if the air supply fails
5) There is no 'overpressure' limits in the system
6) Exhaust air filters need to be added to prevent particles from being emmitted
7) No additional 02 supply port would need to be connected
8) The air valves should be Oxygen Safe - so ideally made of brass

## Hardware
1) The base is made of wood
2) The valves are 12 1/4 inch solenoid valves
3) The air bags are called 'Air Wedges' and are typically used to open car doors
 - this means they can handle large pressures and repeated usage

![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1255.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1256.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1257.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1262.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1263.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1264.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1265.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/hardware/IMG_1266.jpg)

## Electronics
1) Breadboard plug and play electronics for quick prototyping
2) The bag 'high' and bag 'low' detectors are simple reed switches
3) The powersupply is 12volts and a DC 2 DC converter creates a 5 volt supply to power the arduino (it is possible that this could be removed and the arduino powered directly by the 12 volts supply - however this way I'm fine with pluggin in my laptop whilst powering the supply)
4) An arduino nano was selected for the CPU as it's cheap and available

![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/electronics/IMG_1258.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/electronics/IMG_1259.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/electronics/IMG_1260.jpg)
![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/electronics/IMG_1261.jpg)

## Software (Arduino Nano Code)
1) The initial code is included in the folder.
2) Note the code needs to be enhanced to control the flow better

```
int valve1 = 2;
int valve2 = 3;
int valve3 = 4;
int intakeHighPin = 5;
int intakeLowPin = 6;

int time_change = 100;
int time_on = 800;

int OnTime = 0;
int OnTimeMax = 6000;

void setup() 
{ 
  pinMode(valve1, OUTPUT);
  pinMode(valve2, OUTPUT);
  pinMode(valve3, OUTPUT);
  pinMode(intakeHighPin, INPUT);
  pinMode(intakeLowPin, INPUT);
  Serial.begin(115200);
} 


void loop() 
{ 
  Serial.println("starting");
  digitalWrite(valve1, LOW);
  digitalWrite(valve2, LOW);
  delay(time_change);
  digitalWrite(valve1, HIGH);
  delay(100);              

  while((digitalRead(intakeHighPin) == HIGH) && (OnTime < OnTimeMax)) {
    //While loop that SHOULD end if the input goes low
    
    Serial.println("loop");
    delay(100);                                               
    // wait 100 ms
    OnTime = OnTime + 100;
  }
  OnTime = 0;
  
  Serial.println("end");
  
  digitalWrite(valve3, LOW);
  digitalWrite(valve1, LOW);
  delay(time_change);
  digitalWrite(valve2, HIGH);

  while((digitalRead(intakeLowPin) == HIGH) && (OnTime < OnTimeMax)) {
    //While loop that SHOULD end if the input goes low
    
    Serial.println("loop");
    delay(100);                                               
    // wait 100 ms
    OnTime = OnTime + 100;
  }
  OnTime = 0;
  
  digitalWrite(valve2, LOW);
  delay(time_change);
  digitalWrite(valve3, HIGH);
  delay(time_on*5);
  
} 

```

## Parts List

Note the following parts of examples of what this ventilator was built with. If you can't source exactly these items, this list provides ideas for what materials you could use. Note again that this is an information only prototype and changes in parts could significantly affect the effectiveness of the system. This must be considered experimental vs the exact parts needed for a system.

* [Air Wedges](https://www.amazon.com/gp/product/B081YQ4HRK) - NovelBee Car Air Pump Wedges Alignment Tool,Medium and Small Inflatable Air Shim Bag Pump with Valve and Two Plastic Window Wedge for Auto Repair and Home Use
* [Air Connectors](https://www.amazon.com/gp/product/B07L1FVKPJ) - 1/4" Tube OD x 1/4" NPT Thread Male Straight Connector Push to Connect Pneumatic Tube Fitting
* [Air Connectors](https://www.amazon.com/gp/product/B07JLXR3V6) - 6 Style 6mm Push to Connect Tube Fitting Assortment Kit, Including PL-1/4-N1, PL-1/4-N2, PC-1/4-N1, 1/4 inch od, 1/4 inch Od Y Spliter, PUC-1/4 Push to Connect Tube Fitting
* [TIP120 NPN Power Transistors](https://www.amazon.com/gp/product/B07LG2C3MY) - Bridgold 20pcs TIP120 TO-220 NPN Darlington Bipolar Power Transistor, 5A 60V HFE:1000, 3-Pin
* [Breadboard](https://www.amazon.com/gp/product/B077DN2PS1) - Breadboard Solderless Prototype PCB Board – ALLUS BB-009 (3pcs) 400 Pin with 4 Power Rails and Double Sided Tape for Raspberry Pi and Arduino
* [Valves](https://www.amazon.com/gp/product/B074Z5SDG3) - 1/4inch DC 12V 2 Way Normally Closed Electric Solenoid Air Valve
* [Arduino](https://www.amazon.com/gp/product/B07G99NNXL) - LAFVIN Nano V3.0, Nano Board ATmega328P 5V 16M Micro-Controller Board Compatible with Arduino IDE (Nano x 3 with USB Cable)
* [Air Tubes](https://www.amazon.com/gp/product/B07VGGLCYV) - Tailonz Pneumatic Air Line 1/4 inch od Pneumatic Nylon Tube 32.8ft Air Brake Tubing Nylon Hose Kit

## Important Links

* [UK Ventilator Specs](https://www.britishchambers.org.uk/media/get/Specification%20For%20RMVS%20Challenge.pdf) - Published in UK


## Contact
hackadayrex@gmail.com

