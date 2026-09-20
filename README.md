# Analog-Bandgap-Reference using Sky 130 PDK
A bandgap voltage reference is a voltage reference circuit used in integrated circuits. It produces an almost constant voltage corresponding to the particular semiconductor's theoretical band gap, with very little fluctuations from variations of power supply, electrical load, time, temperature (as of 1999, they typically have an initial error of 0.5–1.0% and a temperature coefficient of 25–50 ppm/°C).[1]
### Introduction to Band gap reference
Typically, Integrated circuits or SoC's have various analog and Digital subsystems that require various supply voltages which is being provided by LDO's. These LDO's are in turn provided by independent biasing ( Process-Voltage - Temperature). For a required Vref=1V, the Tempco = 10-50ppm/degree C and PSRR= 40-60 dB. 
Basically, the generation of reference voltage can be done by 
#### Voltage divider network - This has good temperature co-efficient, but sensitivity is unity.
#### Forward biased pn junction - It has temperature coefficient of 2233ppm/degree centigrade and sensitivity is less than unity
#### Base Emitter Voltage referenced circuit - is the improved version of above ones which has a good PSRR but temp coefficient =2333ppm/degree C.
The best solution is to have Bandgap reference which consists of negative voltage and positive voltage that gets added up to give a reference voltage for temperature coefficient of 10 - 50ppm/degree centigrade. 

![Bandgap reference](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/Bandgap%20reference.png) 

#### Introduction to Bandgap Reference
A Bandgap reference is integrated in bulk CMOS or in transistor technologies without any external components.
Significance of Bandgap reference:
- Low Dropout regulators
- Analog to Digital Converters
- DC to DC Buck Converter
- Digital to Analog Converter

###Types of Bandgap Reference [BGR]
Based on Architecture
- Self biased Current Mirror
- Operational Amplifier
Based on Application
- Low Voltage BGR
- Low Power BGR
- High PSRR and low noise BGR
- Curvature compensated BGR
####Different Components of Bandgap Reference are
- CTAT voltage generation circuit
- PTAT voltge generation circuit
- Self biased current mirror circuit
- reference branch circuit
- Startup circuit
####The software used in this workshop:
- NgSpice - Circuit Simulation
- Magic - Layout
- Netgen - LVS and Post layout

#### Analysis of CTAT Voltage generation circuit
![CTAT voltage gen](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/CTAT%20voltage%20gen.png)
![ CTAT voltage generation code](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/CTAT%20volatge%20generation_code.png)
The analysis of CTAT voltage generation with single unit transistor and multibit transistor is shown below. The single bit gives less negative slope i.e. -1.745mV/degree C and with multibit transistor gives -1.914mV/degree C.
![CTAT voltage generation ](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/CTAT%20voltage%20generation.png)
The graph below shows the CTAT voltage generation with variable currents.
![CTAT voltage generaion variable current](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/CTAT%20voltage%20gen%20with%20variable%20current.png)
#### PTAT Voltage Generation
The basic voltage generation circuit is as shown below:
![PTAT_Voltage_q1](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/PTAT_Voltage_q1.png)
![PTAT Voltage Generation](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/PTAT%20Voltage%20Generation.png)
The code for PTAT voltage generation is as shown below:
![PTAT voltage generation](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/PTAT%20voltage%20generation.png)
### Analysis of PTAT Voltage generation:
- plot v(qp1) = -1.654mV which is similar to CTAT.
- plot v(qp1) v(ra1) = -1.66mV
- plot v(qp2) = -1.87mV
- plot v(ra1) - v(qp2) = 187microV which is a PTAT
- plot vid1#branch vid2#branch are overlapped
  
The final results for the above plots is as shown below
![PTAT_Voltage_q1](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/PTAT_Voltage_q1.png)

![PTAT_results](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/PTAT_results.png)

![PTAT voltage generation final results](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/PTAT%20voltage_generation_final%20results.png)
#### BGR using Ideal OP-AMP
- For DC simulation op-amp is fine
- plot v(qp1) v(ra1) is same
- current of that branch i.e. vid1#branch vid2#branch is also same
- plot v(qp3) = -1.65mV is a CTAT voltage
- plot v(vref) -v(qp3) = 1.65mV is a PTAT voltage
- plot v(vref) is a curve with 32ppm
![BGR_using_ideal_opamp_analysis](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/BGR%20using%20ideal%20opamp_analysis.png)
![BGR_using_idealopamp](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/BGR%20using%20ideal%20opamp.png)
#### BGR using Self biased current mirror circuit
- For transient simulation we perform self-biased current mirror is used

### Layout Design
#### LVS and Post layout
