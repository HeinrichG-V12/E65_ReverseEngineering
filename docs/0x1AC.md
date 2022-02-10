# CAN ID 0x1AC Status ARS:
- Type: CAN Standard
- ID: 0x1AC
- DLC: 4
- Tx method: cycle
- Cycle time: 20ms

|Signal|Start bit|Length|Order|Value type|Factor|Offset|Unit|
|------|---------|------|-----|----------|------|------|----|
|ALIV_COU_ARS|8|4|Intel|Unsigned|1|0||
|ST_CLCTR_ARS|12|2|Intel|Unsigned|1|0||
|TORQ_TAR_ARS|16|8|Intel|Unsigned|0.5|0|Nm|
|TORQ_AVL_ARS|24|8|Intel|Unsigned|0.5|0|Nm|

- TORQ_TAR_ARS, torque target

- TORQ_AVL_ARS, torque actual value

Message example:
- 0x1AC 4 02 17 04 06
    - ALIV_COU_ARS: 7
    - ST_CLCTR_ARS: 1
    - TORQ_TAR_ARS: 2Nm
    - TORQ_AVL_ARS: 3Nm