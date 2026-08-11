# CHAOS_Heat_Pump_2026_Summer

Welcome! This repository covers my design process for the heat pumps I made during summer 2026 at Princeton University. The goal of this repo is to
1. Show how I built the electrical system from start to finish
2. Add files for the low and high level code needed to control the heat pump (low for particle operation, high level for openBOS operation) 
3. Show how to setup up other essential components of the heat pump like the water tanks
5. Allow for those interested in building miniature heat pump systems to have a guide on the systems and controls side of it

# Part 1: Electronics

In this section, I will cover the physical layout of the circuitry, along with a guide on the parts.

First, here is an image of the air-water heat pump's circuitry:
<img width="4032" height="3024" alt="Heat Pump Circuitry" src="https://github.com/user-attachments/assets/ad885113-26b2-4dd8-8313-b50ac99cac92" />
Here are the notable components:
- [Screw Terminal](https://www.amazon.com/YUKKOEOQ-Positions-Pre-Insulated-Insulated-Connector/dp/B0FFGVBY26/ref=pd_sbs_d_sccl_1_1/146-4497402-1289054?pd_rd_w=0murg&content-id=amzn1.sym.aa738fbd-ad05-4d11-aae2-04b598db6305&pf_rd_p=aa738fbd-ad05-4d11-aae2-04b598db6305&pf_rd_r=T772Q91SB8AHZTSWFTEZ&pd_rd_wg=QfdGC&pd_rd_r=d543f15e-7fd4-438a-b933-3fefb6fb9d84&pd_rd_i=B0FFGVBY26&th=1)
  - This acts as the main power distribution for my circuit. Every device is directly connected to the 24 V screw terminal. The only exceptions include the particle argon, which accepts up to 5 V via its buck converter, along with the many 12 V devices, which use another type of screw terminal (which works similarly).
  - Screw terminals work in separated columns. You must connect the columns yourself using wire.
  - Here is an example:
<img width="740" height="602" alt="image" src="https://github.com/user-attachments/assets/5333ef50-df75-416e-a98f-b5590ca48290" />

- Buck converters
  - These are able to cleanly step down voltage. Simply put the input side on input (in my case 24 V) and you can adjust the output voltage using a potentiometer
  - The difference is that the XL4015 can handle a higher amperage flowing through the circuit
- [MOSFETS](https://www.amazon.com/High-Power-Adjustment-Electronic-Controller-Brightness/dp/B0FMJH3DML/ref=pd_ci_mcx_di_int_sccai_cn_d_sccl_1_1/134-1598245-9390340?pd_rd_w=q6Tjo&content-id=amzn1.sym.751acc83-5c05-42d0-a15e-303622651e1e&pf_rd_p=751acc83-5c05-42d0-a15e-303622651e1e&pf_rd_r=ADHR8YRACH0N93X7BNET&pd_rd_wg=fuv9y&pd_rd_r=8bf14c1c-f220-4da3-bbdc-736db1d18533&pd_rd_i=B0FMJH3DML&psc=1)
   - Variable voltage, mainly used on water pumps to modulate speed
   - Not necessarily a clean signal, switch turns on and off at a certain pace, allowing you to modulate from 0 V all the way to your input voltage
   - Modulate using pwm signal
- [PWM to Analog Converter](https://tinkersphere.com/electronic-components/2980-pwm-to-analog-converter-module.html?srsltid=AfmBOoqBeFCTH-jJtcLuXnP2rVsC9qjX1O_KOffNygqXqgoI-gh9lbyM0jI)
  - Used to modulate output voltage from either 0-3.3 V or 10 V (can switch using the little shunt resistor on the PCB)
  - Clean signal, is used to modulate heat pump speed
