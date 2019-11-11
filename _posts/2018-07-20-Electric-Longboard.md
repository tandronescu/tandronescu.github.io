---
title: Electric Longboard
date: 2018-07-20
tags: [electrical, mechanical, motor, battery]
header:
    image:
---

After many hours of research, ordering parts, assembly and troubleshooting my electric longboard completed its first few trial runs as shown in the videos below.

<div align="center">
<iframe src="https://drive.google.com/file/d/1Se2hRxlJoFCT2OBcwbA-a0FGnyRDdGKp/preview" width="640" height="480"></iframe>
<br />
<iframe src="https://drive.google.com/file/d/1o4h1cIwPDnE405XYR6Z-vpOI-E71b0Ps/preview" width="640" height="480"></iframe>
</div>

## Key Points for Summary
* Top Speed: ~30km/h and Range: ~50km
* 6S2P Lithium Polymer Battery Configuration (~22.2V and 10Ah capacity)
* 190KV Brushless Outrunner Motor, 2.25 gear ratio with 12mm wide pulley
* FOCBOX Motor Controller 120A Peak Current Limit 60A Continuous Limit
* Nano-X 2.4GHz Receiver and Transmitter
* Industrial Strength Velcro to attach components to deck
* Threaded inserts and screws to secure enclosure to deck

In order to breakdown the components of this electric longboard into more detail I have organized them into the following categories: electrical, drivetrain, deck/enclosure.

## Electrical

The electrical components power the board and also allow for control of the motor in terms of accelerating and decelerating. The overall wiring diagrams are shown below:
<br />
![Battery Wire Diagram](/images/Battery_Wire_Diagram.jpg)
![Balance Wire Diagram](/images/Balance_Wire_Diagram.jpg)

The two main choices for batteries are usually lithium-polymer (lipo) or lithium-ion (lion). Lion batteries are more prone to voltage sag (voltage drops quickly for a short period of time under heavy discharge, then goes back up to slightly less than where it was originally) so they are better in large packs where this effect can be mitigated. Lipo batteries are much better with regard to voltage sag so smaller packs are feasible. 

The general rule of thumb is putting more batteries in series results in higher voltage and hence more power/torque and a higher top speed. Placing more batteries in parallel increases overall capacity and hence the range of the board on a singular charge. 

I bought 4 3S (3 cells in series, each cell being ~3.7V for a total of ~11.1V per pack) lipo batteries. This gave me some flexibility in terms of their arrangement. I could pick 6S with 2 spare batteries, 6S2P (shorthand for 6 cells in series in parallel with another 6 cells in series), 9S with 1 spare battery or 12S. 

I chose to go with a 6S2P configuration because I was aiming for more range and less power for this particular build: 
<br/><br/>
![Lipo Batteries](/images/batteries.jpg)

Two sets of two battery packs were connected in series and their main/balance leads were both connected to a parallel charging board: 
<br/><br/>
![Parallel Board](/images/parallel_board.jpg)

From the balance board, the output is split in parallel with one branch dedicated to the charger and one branch dedicated to powering the motor controller. Since the enclosure is screwed on, it is much easier if the batteries can be plugged into the charger while remaining inside the enclosure. One of the parallel branches from the output can be pulled out of an opening in the enclosure along with the balance leads to quickly plug into the charger stationed anywhere outside the board. 

The other parallel branch powers the FOCBOX motor controller which is a motor controller specifically designed for electronic longboard applications and runs on the [open source firmware](http://vedder.se/) and GUI developed by Ben Vedder. 
<br/><br/>
![Vesc](/images/vesc.jpg)

It has 2 modes of operation, BLDC and FOC, I choose to use FOC because it is quieter and has smoother operation. The current limits for the battery and motor were adjusted appropriately for safe and efficient operation. 

An on-off mechanism was also necessary and it made the most sense to put it on this branch of the circuit where it could be accessible from the side of the enclosure if holes were drilled. This way the board could easily be turned on for use and off when not in use to preserve battery. I used AS150 anti-spark connectors to reduce the amount of sparking when the system was turned on. The wire is soldered on the ends of the male and female connectors which are screwed into plastic housings.
<br/><br/>
![AS150 Anti-Spark Connectors](/images/as150.jpg)

The motor controller then has 3 phase wires which connect directly to the 190KV Brushless Outrunner Motor. The bullet connectors from the motor controller and the motor phase wires did not match in size so I soldered together makeshift adapters using 90 degree sections from multimeter test leads which created a tight seal while still allowing for easy detachment. One of my goals was to make this project as modular as possible to allow for upgrades and altercations in the future. 
<br/><br/>
![Phase Wires](/images/phase_wires.jpg)

Finally a Nano-X transmitter/receiver pair are used to control the longboard once it is in operation. It can accelerate and decelerate using a throttle control. 

## Drivetrain

The drivetrain consists of a motor pulley, wheel pulley, drive belt and motor mount. The main objective of the drivetrain is to generate as much torque as possible because a lot of power is needed to move the combined weight of a human and longboard, especially when hills are involved. Moreover, this is a single drive design meaning the wheel with the motor attached to it is providing all the power as the other 3 wheels will simply move in response once the longboard gets going. To achieve a high level of torque a small gear is attached to the motor (16 teeth) and a large gear is attached to one of the longboard wheels (36 teeth). 
<br/><br/>
![Pinion Gear](/images/pinion.jpg)

The high rpm from the motor is converted into more torque for the wheel. The two gears are connected via drive belt which is a strong rubber-fibre glass composite. The motor is connected to the longboard trucks using a motor mount as pictured below:
<br/><br/>
![Motor Mount](/images/motor_mount.jpg)

## Deck/Enclosure

The last element to consider is how to keep all the electrical components under the deck and dampen the effects of vibration on them. Furthermore, an enclosure was needed to protect the electronics from water and various debris while riding the longboard. 

I attached all the components directly to the deck using industrial strength velcro. The connection is very secure and the components can still be removed for inspection or changes, again attempting to have more modularity.

To attach the enclosure, I used threaded inserts installed directly into the wood longboard deck.
<br/><br/>
![Threaded Insert](/images/threaded_insert.jpg)

The enclosure has 6 holes drilled along its edges and screws are used to secure it to the deck.
![Enclosure](/images/enclosure.jpg)






