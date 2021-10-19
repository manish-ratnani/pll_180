![mas](https://user-images.githubusercontent.com/92747247/137858130-74e6f2e8-cd55-4c0a-a6aa-66a41eea142b.jpg)
This is intense workshop to design PLL using 180nm PDK, steps > design, simulate, layout and finally tapeout  
---

## Table of contents

- [PLL_OSU180nm_VSD](#pll_osu180nm_vsd)
  - [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Design Specifications](#design-specifications)
  - [Tools used](#tools-used)
  - [Theory](#theory)
    - [Phase Locked Loop](#phase-locked-loop)
      - [Clock multiplier using PLL](#clock-multiplier-using-pll)
      - [Our implementation](#our-implementation)
      - [Phase frequency detector](#phase-frequency-detector)
      - [Charge pump and RC filter](#charge-pump-and-rc-filter)
      - [Voltage Controlled Oscillator](#voltage-controlled-oscillator)
      - [Frequency divider](#frequency-divider)
- [Pre-layout simulation](#pre-layout-simulation)
    - [1) Inverter (example)](#1-inverter-example)
      - [Esim netlist](#esim-netlist)
      - [Modifications](#modifications)
      - [Running simulation](#running-simulation)
    - [3) NAND gates](#3-nand-gates)
      - [2 input NAND](#2-input-nand)
      - [3 input NAND](#3-input-nand)
      - [4 input NAND](#4-input-nand)
    - [3) Phase detector](#3-phase-detector)
    - [4) Phase detector with RC filter and charge pump](#4-phase-detector-with-rc-filter-and-charge-pump)
    - [5) Voltage Controlled Oscillator](#5-voltage-controlled-oscillator)
    - [6) Clock divider](#6-clock-divider)
    - [Pre-layout simulation of whole circuit](#pre-layout-simulation-of-whole-circuit)


---

## Design Specifications 
| Parameter| Description| Min | Type | Max | Unit | Condition |
| :---:  | :-: | :-: | :-: | :---:  | :-: | :-: |
|VDD|Digital supply voltage||1.8||V|T=-40 to 150C|
|FCLKREF|Reference clock frequency|5|10|12.5|MHz||	
|FCLKOUT|Output clock frequency|39.7|80.91|99.81|MHz|PLL mode, T=27C, VDD=1.8|
|FCLKOUT|Output clock frequency||||MHz|VCO mode, T=27C, VDD=1.8|
|DC|Duty Cycle|48||52|%|T=-40 to 150C|
|IBCP|Bias current for VCO||||uA||
|VVCO|Oscillatror control input voltage|.557||0.62|V|Vin_vco = 0V at t = 0 (.uic)|
|JRMS|Jitter (rms)||future work||ps|PLL mode, FCLKREF = 10MHz|
|TSET|Settlng Time|5.2|5|4.6|us|start from EN_CP and report 2 values; one at FCLKOUT=40MHz and one at FCLKOUT=100MHz|
|CL|Load Capacitance||||pF||
|IDDA|Analog Supply current||||ua|VVCO=0.8V, VCO mode|
|IDDA|Analog Supply current||||ua|FCLKREF=10MHz, PLL mode|
|IDDA|Analog Supply current||||pa|EN_VCO=0, EN_CP=0, FCLKREF=0|
|IDDD|Digital Supply Current||||uA|VVCO=0.8V, VCO mode|
|IDDD|Digital Supply Current||||uA|FCLKREF=10MHz, PLL mode|
|IDDD|Digital Supply Current||||uA|EN_VCO=0, EN_CP=0, FCLKREF=0|

## Basic inverter simulation 
# Pre-layout simulation

Pre-layout simulation is done using ngspice netlists generated from esim.

---

### 1) Inverter (example)

The netlist generated from esim looks like this : 

File : [```documents/inv101.cir```](documents/inv101.cir)
```
