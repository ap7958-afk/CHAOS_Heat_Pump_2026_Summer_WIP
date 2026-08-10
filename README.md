# CHAOS_Heat_Pump_2026_Summer
# Introduction
This project includes documentation on revitalized heat pumps in the CHAOS Lab, focusing on the electrical hardware and code.

Welcome! This repository covers my design process for the heat pumps I made during summer 2026 at Princeton University. The goal of this repo is to
1. Show how I built the electrical system from start to finish
2. Add files for the low and high level code needed to control the heat pump (low for particle operation, high level for openBOS operation) 
3. Show how to setup up other essential components of the heat pump like the water tanks
5. Allow for those interested in building miniature heat pump systems to have a guide on the systems and controls side of it

# Part 0.5: The Mechanical Side

During my internship, I focused less on this part. When I entered the lab, my goal was to revitalize two heat pumps that were built, but not being used. The heat pump systems mechanically are not very complex. Both the air to water and water to water systems include a compressor (motor), condenser (generates hot), expansion valve (maintains hot and cold difference), and evaporator (cold side). Refrigerant flows in this direction, as the compressor sucks refrigerant from the cold evaporator, and sends it to the hot condenser. The water to water system also has a filter drier to remove debris, as well as a site glass to inspect for air trapped inside the copper tubes (which is not relevant when operating the heat pump). 
