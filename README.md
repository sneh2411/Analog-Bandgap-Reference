# Analog-Bandgap-Reference using Sky 130 PDK
A bandgap voltage reference is a voltage reference circuit used in integrated circuits. It produces an almost constant voltage corresponding to the particular semiconductor's theoretical band gap, with very little fluctuations from variations of power supply, electrical load, time, temperature (as of 1999, they typically have an initial error of 0.5–1.0% and a temperature coefficient of 25–50 ppm/°C).[1]
### Introduction to Band gap reference
Typically, Integrated circuits or SoC's have various analog and Digital subsystems that require various supply voltages which is being provided by LDO's. These LDO's are in turn provided by independent biasing ( Process-Voltage - Temperature). For a required Vref=1V, the Tempco = 10-50ppm/degree C and PSRR= 40-60 dB. 
Basically, the generation of reference voltage can be done by 
#### Voltage divider network - This has good temperature co-efficient, but sensitivity is unity.
#### Forward biased pn junction - It has temperature coefficient of 2233ppm/degree centigrade and sensitivity is less than unity
#### Base Emitter Voltage referenced circuit - is the improved version of above ones which has a good PSRR but temp coefficient =2333ppm/degree C.
The best solution is to have Bandgap reference which consists of negative voltage and positive voltage that gets added up to give a reference voltage for temperature coefficient of 10 - 50ppm/degree centigrade. 

![Bandgap reference](https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/Bandgap%20reference.png) alt="Bandgap reference" width="400" height="300">.
<img width="300" height="200" alt="image" src="(https://github.com/sneh2411/Analog-Bandgap-Reference/blob/main/Bandgap%20reference.png)" />
### Day 1 – Introduction to FPGA Architecture, Programming and Vivado Design Flow using Basys board. 
## Objective

The objective of Day 1 was to understand the fundamentals of FPGA architecture, FPGA design flow, and implementation of a simple digital design using Xilinx Vivado on the Basys 3 FPGA board and remotely too

#### Introduction to FPGA (Field Programmable Gate Array)
A field-programmable gate array (FPGA) is a type of configurable integrated circuit that can be repeatedly programmed . 

Significance of FPGA:
- Hardware acceleration
- Signal processing
- Embedded systems
- Machine learning
- Aerospace systems
- High-performance computing

## Comparison  

Feature| FPGA | ASIC |
|---|---|---|
Design Process| simpler design | long and complex
Flexibility| Reprogrammable | Fixed after fabrication |
Time to market| Faster prototyping | Long fabrication cycle |
Cost| Lower initial cost | High initial fabrication cost |
Performance| slower but more versatile | faster and more efficient |
Hardware Design| RTL to Bitstream | RTL to Layout |

---
### The complete flow for a FPGA Programming on Vivado:
- Simulation
  ![Simulation_Counter](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/154bce8823589f8bde3c9c76d8171f75f6857e01/Simulation_Counter.png)
- Elaboration Verilog HDL into an RTL schematic representation.

   ![Pinassignmentsetup](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Pinassignmentsetup.png)
- Synthesis
- ![Synthesis](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/RTL%20Schematic.png)
- Implementation
  
- Timing analysis
- ![Design_Timing Summary](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Design_Timing%20Summary.jpg)

- Power analysis gives dynamic,static,clock and signal power
- ![Poweranalysis_report](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Power%20analysis_report.png)

- Resource utilization
- ![Resource](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Resource_Utilization_report.png)
- Constraints and pin mapping
![Constraint_file](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Constraint_file.png)

# Virtual Input/Output (VIO)

Virtual Input/Output (VIO) allows internal FPGA signals to be monitored and controlled in real-time using Vivado Hardware Manager.

# Day 2 - Study on OpenFPGA, VPR and VTR Flow

Day 2 focused on understanding the open-source FPGA CAD flow Tools:
- OpenFPGA
- VPR (Versatile Place and Route)
- VTR (Verilog-To-Routing)

The complete flow from Verilog RTL to FPGA routing and timing analysis was explored. Timing constraints, post-synthesis simulation, power analysis and generated reports were also studied.

## VPR Visualization

![VPR_Visualisation](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/VPR_Visualisation.png)

---

### EArch FPGA Architecture Analysis using VPR

There are about more than 20 architecture of that #EArch.xml# FPGA architecture file was analyzed using the VPR flow. The architecture visualization, routing resources, nets, logical connections and timing reports were generated and studied.
### Nets Analysis - net connections after routing

![Nets report](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Nets%20report.png)

### Logical Connections Report
![LogicalConnections](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Logical%20Connections.png)


### Critical Path Analysis Report
## Routing Utilization Report
![Critical Path Analysis ](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Critical%20Path%20Analysis.png)

![RoutingUtilization_Report](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Routing%20Utilization_report.png)
## Timing Analysis before using constraints
![Setup_Timing_bc](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Setup_Timing_bc.png)
![Hold_Timing_bsdc](https://github.com/sneh2411/FPGA-Fabric-Design-and-Architecture/blob/main/Hold_Timing_bsdc.png)
# Timing Analysis using Constraints

Timing constraints were added using an SDC file. The constraints file gives Clock period,Input and Output delays

## SDC Constraint File
