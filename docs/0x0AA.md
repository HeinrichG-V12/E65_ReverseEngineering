# CAN ID 0x0AA Torque 3:
- Type: CAN Standard
- ID: 0x0AA
- DLC: 8
- Tx method: cycle
- Cycle time: 10ms

|Signal|Start bit|Length|Order|Value type|Factor|Offset|Unit|
|------|---------|------|-----|----------|------|------|----|
|CHKSM_TORQ_3_DME|0|8|Intel|Unsigned|1|0||
|ALIV_TORQ_3_DME|8|4|Intel|Unsigned|1|0||
|TORQ_DVCH|12|12|Intel|Signed|0.5|0|Nm|
|ANG_ACPD|24|8|Intel|Unsigned|0.39063|0|%|
|RPM_ENG|32|16|Intel|Unsigned|0.25|0|1/min|
|RPM_ENG_ERR|48|2|Intel|Unsigned|1|0||
|ST_IDLG_ENG|50|2|Intel|Unsigned|1|0||
|ST_CLCTR_V|52|4|Intel|Unsigned|1|0||
|RQAM_FU|56|8|Intel|Unsigned|1|0||

- ANGL_ACPD: accelerator pedal angle

|Value|Description|
|-----|-----------|
|0x00|unpressed|
|....|value|
|0xFF|pedal on the floor|

- RPM_ENG_ERR:

|Value|Description|
|-----|-----------|
|0x0|signal clear and correct|
|0x1|speed sensor defective|
|0x3|signal invalid|

- ST_IDLG_ENG:

|Value|Description|
|-----|-----------|
|0x0|idle|
|0x1|no idle|
|0x3|signal invalid|

- ST_CLCTR_V:

|Value|Description|
|-----|-----------|
|0x0|acc regulation, pedal not pressed|
|0x1|acc regulation, pedal pressed|
|0x4|cc regulation, retard|
|0x5|cc regulation, constant speed|
|0x6|cc regulation, recall|
|0x7|cc regulation, speed up|
|0x8|pedal not pressed|
|0x9|pedal pressed|
|0xA|pedal transgress|
|0xB|pedal kickdown|

Message example:
- 0xAA 8 39 47 02 00 87 0A 80 33
    - CHKSM_TORQ_3_DME: 57
    - ALIV_TORQ_3_DME: 7
    - TORQ_DVCH: 18Nm
    - ANG_ACPD: 0.0000%
    - RPM_ENG: 673.75 1/min
    - RPM_ENG_ERR: 0
    - ST_IDLG_ENG: 0
    - ST_CLCTR_V: 8
    - RQAM_FU: 51 l/h