![mas](https://user-images.githubusercontent.com/92747247/137858130-74e6f2e8-cd55-4c0a-a6aa-66a41eea142b.jpg)
# This is intense workshop to design PLL using 180nm PDK, steps > design, simulate, layout and finally tapeout  
![1](https://user-images.githubusercontent.com/92747247/137857760-232e285c-b013-48b7-a543-f8e31adfa97e.png)
![2](https://user-images.githubusercontent.com/92747247/137858359-d3219052-1b42-4949-8b00-27bd65abda6b.png)
![3](https://user-images.githubusercontent.com/92747247/137858370-07781134-03e9-44a0-a3df-c83c1574ce87.png)
![4](https://user-images.githubusercontent.com/92747247/137858391-b1976453-9fba-4f71-bd13-f3d68f40b918.png)
![6](https://user-images.githubusercontent.com/92747247/137858430-86824013-4350-4ee9-9fec-3aca072ec48b.png)
![7](https://user-images.githubusercontent.com/92747247/137858445-2a238bba-7ddd-40f7-8515-4be9a8d90a39.png)

Design Specifications
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
