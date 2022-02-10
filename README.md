# E65 Reverse Engineering

## Reverse engineering on PT-CAN and Local-CAN of BMW E65/E66 ##
## The main goal of this project is to replace the original engine control (2x DME) with rusEFI Proteus. ##
## The other goal is to find the CAN messages needed for the operation of the installed automatic transmission (ZF 6HP26) to be able to run the transmission stand-alone... ##

## [BMW Standard Tools installation HowTo](https://www.e90post.com/forums/showthread.php?t=1196830)

### Messages needed for the transmission operation ([source](docs/6HP26.pdf),  page 80) ###

|Signals|Transmitter|Receiver|CAN ID|
|-------------------|--------|--------|--------|
|Transmission selector switch|SZL|EGS|[0x192](docs/0x192.md)|
|Terminal status|CAS|EGS|[0x130](docs/0x130.md)|
|Central locking|CAS|EGS|[0x2FC](docs/0x2FC.md)|
|Transmission data|EGS|CAS||
|Engine data|DME / DDE|EGS|[0x1D0](docs/0x1D0.md)|
|Wheel rotating speeds|DSC|EGS|[0x0CE](docs/0x0CE.md)|
|Braking request|EMF|EGS||
|Transmission data display|EGS|Instr. cluster||
|Check Control message|EGS|Instr. cluster||
|Torque request|EGS|DME|[0x0B5](docs/0x0B5.md)|
|Operating voltage|Power Module|EGS|[0x3B4](docs/0x3B4.md)|
|Stationary consumers|EGS|Power Module||

### CAN-IDs in PT-CAN BMW E65 with MED 9.2.1 ###

|Message name|Transmitter|CAN ID|Message status|
|-----------|-----------|------|------|
|Torque 1|DME1 / DDE1|[0x0A8](docs/0x0A8.md)|fully decoded|
|Torque 2|DME1 / DDE1|[0x0A9](docs/0x0A9.md)|fully decoded|
|Torque 3|DME1 / DDE1|[0x0AA](docs/0x0AA.md)|fully decoded|
|Retard request ACC|ACC|[0x0AD](docs/0x0AD.md)|TBD, partially decoded|
|Torque request EGS|EGS|[0x0B5](docs/0x0B5.md)|fully decoded|
|Torque request DSC|DSC|[0x0B6](docs/0x0B6.md)|fully decoded|
|Torque request ACC|ACC|[0x0B7](docs/0x0B7.md)|fully decoded|
|Transmission data 1|EGS|[0x0BA](docs/0x0BA.md)|fully decoded|
|Steering wheel angle|SZL|[0x0C4](docs/0x0C4.md)|TBD, partially decoded |
|Yaw request 2||[0x0CA](docs/0x0CA.md)|TBD|
|Yaw answer 2||[0x0CB](docs/0x0CB.md)|TBD|
|Wheel speed|DSC|[0x0CE](docs/0x0CE.md)|fully decoded|
|Terminal status|CAS|[0x130](docs/0x130.md)|fully decoded|
|Display ACC|ACC|[0x190](docs/0x190.md)|TBD|
|Operation transmission selector switch|SZL|[0x192](docs/0x192.md)|TBD, partially decoded|
|Operation cruise control / ACC|SZL|[0x194](docs/0x194.md)|fully decoded|
|Status DSC|DSC|[0x19E](docs/0x19E.md)|fully decoded|
|Speed|DSC|[0x1A0](docs/0x1A0.md)|fully decoded|
|Transmission data 2|EGS|[0x1A2](docs/0x1A2.md)|fully decoded|
|Status ARS|ARS|[0x1AC](docs/0x1AC.md)|fully decoded|
|Status instrument cluster|Kombi|[0x1B4](docs/0x1B4.md)|fully decoded|
|Engine data 1|DME|[0x1D0](docs/0x1D0.md)|fully decoded|
|Display gearbox data|EGS|[0x1D2](docs/0x1D2.md)|TBD|
|Speed cruise control|DME|[0x200](docs/0x200.md)|TBD, partially decoded|
|Damper current|EDC-K|[0x322](docs/0x322.md)|TBD|
|Status damper programm|EDC-K|[0x326](docs/0x326.md)|TBD, partially decoded|
|Mileage|Kombi|[0x330](docs/0x330.md)|fully decoded|
|Display RPM range|DME|[0x332](docs/0x332.md)|fully decoded|
|Power management charge voltage|PM|[0x334](docs/0x334.md)|fully decoded|
|Vehicle identification number|CAS|[0x380](docs/0x380.md)|fully decoded|
|Electronic engine oil dipstick|DME|[0x381](docs/0x381.md)|TBD, partially decoded|
|Vehicle type|CAS|[0x388](docs/0x388.md)|TBD, partially decoded|
|Starting speed|DME|[0x38E](docs/0x38E.md)|fully decoded|
|Operation chasis||[0x398](docs/0x398.md)|TBD|
|Power management battery voltage|PM|[0x3B4](docs/0x3B4.md)|fully decoded|

### Module names: ###
- ACC: active cruise control
- CC: cruise control
- DME: digital motor electronic (gasoline engine)
- DDE: digital diesel electronic (diesel engine)
- EGS: electronic transmission control
- CAS: car access system
- DSC: dynamic stability control
- SZL: switch center steering wheel
- EMF: electromechanical parking brake
- Kombi: instrument cluster
- PM: power module
- EDC-K: electronical damper control

### Some interesting links: ###

- https://www.e90post.com/forums/showthread.php?t=177272&page=7
- https://github.com/commaai/opendbc
- http://bobodyne.com/web-docs/robots/MINI/CAN/Presentation/index.html