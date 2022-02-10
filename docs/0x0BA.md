# CAN ID 0xBA Torque request ACC:
- Type: CAN Standard
- ID: 0x0BA
- DLC: 8
- Tx method: cycle
- Cycle time: 20ms

|Signal|Start bit|Length|Order|Value type|Factor|Offset|Unit|
|------|---------|------|-----|----------|------|------|----|
|ST_GR_GRB|0|4|Intel|Unsigned|1|0||
|ST_GRLV_ACV|4|2|Intel|Unsigned|1|0||
|ST_CCLT|6|2|Intel|Unsigned|1|0||
|GRDT_REIN|8|12|Intel|Unsigned|0.125|0|1/min|
|CHKSM_GRB|40|8|Intel|Unsigned|1|0||
|ALIV_GRB|48|4|Intel|Unsigned|1|0||
|ST_MOD_GRB|52|3|Intel|Unsigned|1|0||
|ST_HYPP_ACV|56|2|Intel|Unsigned|1|0||

- ST_GR_GRB: target gear information from ETCU

|Value|Description|
|-----|-----------|
|0x0|reserved|
|0x1|N|
|0x2|R|
|0x3|P|
|0x4|reserved|
|0x5|1. gear|
|0x6|2. gear|
|0x7|3. gear|
|0x8|4. gear|
|0x9|5. gear|
|0xA|6. gear|
|0xF|signal invalid|

- ST_GRLV_ACV: status gear-shif

- ST_CCLT: status torque-converter-lockup clutch

|Value|Description|
|-----|-----------|
|0x0|disengaged|
|0x1|controlled|
|0x2|closed|
|0x3|signal invalid|

- GRDT_REIN: gearbox-drive-train reinforcement

- ST_MOD_GRB: status mode gearbox

- ST_HYPP_ACV: Status hydraulic-pump active (ssg only)

Message example:
- 0xBA 8 03 FF 0F 00 00 48 8B EF
    - ST_GR_GRB: 3
    - ST_GRLV_ACV: 0
    - ST_CCLT: 0
    - GRDT_REIN: 511.8750 1/min
    - CHKSM_GRB: 48
    - ALIV_GRB: B
    - ST_MOD_GRB: 0
    - ST_HYPP_ACV: 3