# The Rex Ventilator

## !! Warning everything in this repository is for information purposes only !!

[![Rex Ventilator](https://github.com/hackadayrex/ventilator/blob/master/images/video_thumbnail.jpg)](https://youtu.be/pFnB-vOWQmU "Rex Ventilator")

## Important
1. The material contained herein is for informational purposes only and should not be construed as a substitute for professional medical advice, diagnosis or treatment. ANY AND ALL USAGE OF THESE PLANS AND IDEAS, AND ANY DERIVATIONS AND MODIFICATIONS HEROF ARE SOLELY AT YOUR OWN RISK AND BY VIEWING THIS INFORMATION YOU HEREBY WAIVE AND RELEASE THE ORIGINAL POSTER FROM, AND YOU AGREE TO DEFEND AND HOLD HARMLESS THE ORIGINAL POSTER WITH RESPECT TO, ANY AND ALL LIABILITY, DAMAGES, LOSSES, AND INJURY OR DEATH THAT MAY RESULT FROM YOUR USE OR DISTRIBUTION OF THE INFORMATION PROVIDED.  
2. Under no circumstances should the material or information contained herein be construed as marketing for any medical device. 
3. The original poster of the material and information contained herein cannot be held responsible for any personal or property damage caused by an individual’s use of such material and information (including serious personal injury or death). 
4. Reliance on this material and any information contained herein is solely at your own risk and the original poster does not take responsibility for any action you may take as a result of your use of such material and information.
5. By taking and/or using any material and information contained herein, you agree that you will use such material and information in a safe and legal manner, consistent with applicable laws and regulations.
6. This is a only a prototype for a medical device, it has not been subject to clinical trials and has not been tested for safety or effectiveness, therefore it is not, and should not be viewed as, an alternative to any similar FDA approved device.


## Project Status in relation to UK British Chambers of Commerce Specifications

*This design in relation to the UK British Chambers of Commerce specification:* https://www.britishchambers.org.uk/media/get/Specification%20For%20RMVS%20Challenge.pdf

* Be reliable for 14 days: NOT TESTED
* Provide at least two settings for volume of air/air O2 mix delivered per cycle/breath. These settings to be 450ml +/- 10ml per breath and 350ml +/- 10ml per breath. NOT IMPLEMENTED (todo: add additional reed switch for dual volume sweep)
* Provide this air/air O2 mix at a peak pressure of 350 mm H2O. NOT IMPLEMENTED (todo: need specs for connector)
* Have the capability for patient supply pipework to remain pressurised at all times to 150mm H20. NOT TESTED (todo: pressure sensor on patient side that regulates the outlet valve)
* Have an adjustable rate of between 12 and 20 cycles/breaths per minute. NOT TESTED (todo: could be implemented via changing inlet pressure and/or pressure sensing at the air bag)
* Deliver at least 400ml of air/air 02 mix in no more than 1.5 seconds. The ability to change the rate at which air is pushed into the patient is desirable but not essential. NOT TESTED (todo: setup volume testing)
* Be built from O2 safe components to avoid the risk of fire and demonstrate avoidance of hot spots. NOT IMPLEMENTED (todo: update values to brass components)
* Be capable of breathing for an unconscious patient who is unable to breathe for his or herself. Ability to sense when a patient is breathing, and support that breathing is desirable but not es- sential. NOT TESTED (todo: addition of patient side pressure sensor would enable microcontroller to determine if operational)
* Be able to supply pure air and air O2 mix at a range of concentrations including at least 50% and 100% Oxygen. Oxygen shortages are not expected, but the ability to attach a Commercial Off The Shelf (COTS) portable O2 concentrator machine may be a useful feature. NOT IMPLEMENTED (todo: add valve on inlet side to prevent O2 leakage into the air resevoir)
* Support connections for hospital Oxygen supplies – whether driven by piped or cylinder infra- structure. NOT IMPLEMENTED (todo: need specs on typical connectors and/or couplings to 1/4 fittings)
* Be compatible with standard COTS catheter mount fittings (15mm Male 22mm Female). NOT IMPLEMENTED (todo: need specs on typical connectors and/or couplings to 1/4 fittings)
* Fail SAFE, ideally generating a clear alarm on failure. Failure modes to be alarmed include (but are not limited to) pressure loss and O2 loss. NOT IMPLEMENTED (todo: add buzzer to the circuit and trigger if lack of operation at patient pressure monitored, couple with a dismiss button)

This requires $~100 and 4-8 hours to construct.

This is not suitable to support more than one patient using a splitter valve.


# Summary
The Coronavirus is projected to overwhelm the capabilities of most hospital systems during the growth and peak of cases requiring mechanical ventilators. Most ventilators are in short supply and it maybe impossible in many countries to get more. As care is rationed many people are projected to die if not given ventilation at an Intensive Care Unit (ICU). The Rex Ventilator is a prototype design to explore low cost - high availability designs to help fill this gap in the system that would support the breathing of a patient who was unable to breath on their own.

As such, the 'Rex' ventilator is designed to be built from off the shelf parts, be constructed quickly, and be broadly servicable by anyone with basic knowledge of electronics and software design. The Rex would be connected to an air supply (provided by a commercial generator), and then be connected to the patient via intubation. This design is inspired from an earlier 'pandemic ventilor' but added updated controls and an improved air bag design. It is a prototype of a solution that would need further development, but could provide a start point for that work.

The design is made up of three elements:
 - The hardware base
 - Air system (tubes and valves)
 - Electronics and Power supply


# Project Status / Next Steps
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

