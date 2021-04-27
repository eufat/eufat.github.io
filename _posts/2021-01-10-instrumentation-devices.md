---
title: "Instrumentation Devices: Transducer, Micro Electro Mechanical system (MEMS) and DC Motor Operation"
---


## Transducer

A transducer is a device that converts energy from one form to another (for example: from potential energy to electrical energy). Transducers can be applied to change various forms of physical units such as (energy, torque, light, motion, position, etc.) into a form of electrical energy. One of the transducers, for example, is a digital transducer which has a mechanical element coupled with an element that can transfer electricity. Transducers are generally divided into two types, namely active transducers and passive transducers. The element that converts directly into an electrical signal is an active transducer. Meanwhile, passive transducers are elements that require external assistance to respond to changes in energy. Things that must be considered in transducer measurements are range, reapetability, noise and
hysterysis. In this discussion, we will discuss about one of the digital pressure measuring transducers, namely the capacitive pressure transducer.

In a capacitance-based pressure transducer there is a diaphragm, which is a thin metal covered with quartz. The diaphragm which is flanked by two capacitor plates will bend when the pressure port changes its pressure, if the pressure increases, the diaphragm will move upwards and if the pressure drops the diaphragm will move down. If the diaphragm is bent, there will be a change in capacitance between the diaphragm and the capacitor plate. The AC signal that occurs on the plate is used to measure the capacitance.

With the information that Cfs is Full Scale Capacity (the maximum pressure that the transducer can accept), Vex is the Excitation Voltage (recommended voltage difference),Vmeans (measured voltage difference) and CF is the calibration factor.

## Micro Electro Mechanical system (MEMS)


Microelectromechanical systems are devices that integrate mechanical and electrical components that range in size from micrometers to millimeters. MEMS is packaged into IC (Integrated Circuits). MEMS are generally made using silicon, polymer, metal and ceramic materials. There are various kinds of MEMS applications, such as in inkjet printers that use piezoelectrics to detect blood pressure, use pressure sensors that are packaged in MEMS form and in modern cars use sensors in the form of MEMS such as accelerometers, accelerometers are instruments that can measure the acceleration of the system.

The way a capacitor-based accelerometer works, namely this accelerometer measures the acceleration of certain vibrations by changing the capacitance of the fixed outer plates and movable plates, different capacitances at two locations (because the movable plates are located) flanked by two static plates) so that the output voltage changes. To get the measured acceleration from the system above, it can be formulated as follows:

𝑎 = -𝑘(𝑥^2)∆𝐶/2m∈

Where is the spring constant flanking the movable plate, 𝑥1 is the gap distance between the fixed plates and movable plates, 𝑚 is the mass and ∆𝐶 is the capacitance difference between 𝐶2 and 𝐶1.

𝑉𝑥 = (𝐶2 - 𝐶1)𝑉0/(𝐶2 + 𝐶1)

From this equation it can be concluded that the speed is directly proportional to the change in capacitance in the system. Then, the changing capacitance will be directly proportional to the difference in output voltage.

## DC Motor Operation

DC Motor is a motor that uses direct current (DC current) as its power source to move the shaft so that rotation occurs. DC Motor has several important components, namely, a U wire connected to the shaft to drive the motor, two magnets that have different polarity to produce a magnetic field in the wire and a commutator that can reverse the current in the wire. The DC motor works by flowing current from the commutator so that the electric current that flows is perpendicular to the electric field, because this wire is perpendicular to the electric field in different directions so that the Lorentz force acting on the wire is up and down producing torque. The torque that works on the system will move the motor in a rotating manner. The current flowing in the commutator is dividing the voltage by the resistance.

𝐼 = 𝑉/𝑅
Input power resulting from electrical energy will be converted to output power. The output power is the mechanical power that works on the system (torque and angular speed).

𝑃𝑖𝑛 = 𝐼𝑉
𝑃𝑜𝑢𝑡 = 𝑇𝜔 

In addition, to determine the angular velocity, it can be seen from the number of revolutions per minute multiplied by two pi and then divided by 60.

𝜔 = 𝑟𝑝𝑚(2𝜋)/60

However, the input power (Pin) will not always be 100% converted to output power (Pout) because a perfect ideal motor does not exist. Therefore there is an efficiency variable, namely the ratio between input power and output power.

 𝐸 = 𝑃𝑜𝑢𝑡/𝑃𝑖𝑛

The efficiency denoted by 𝐸 is the efficiency that works in a DC motor system, generally a good DC motor has an efficiency of close to 70-80% and a less well-functioning DC motor has an efficiency of between 50- 60%. Higher efficiency means the system can better convert electrical power into the power used to drive the DC motor shaft to move angularly.