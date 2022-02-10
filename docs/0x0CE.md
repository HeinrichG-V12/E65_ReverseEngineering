# CAN ID 0xCE Wheel rotating speed:
- Type: CAN Standard
- ID: 0x0CE
- DLC: 8
- Tx method: cycle
- Cycle time: 20ms

|Signal|Start bit|Length|Order|Value type|Factor|Offset|Unit|
|------|---------|------|-----|----------|------|------|----|
|V_WHL_FLH|0|16|Intel|Signed|0.0625|0|km/h|
|V_WHL_FRH|16|16|Intel|Signed|0.0625|0|km/h|
|V_WHL_RLH|32|16|Intel|Signed|0.0625|0|km/h|
|V_WHL_RRH|48|16|Intel|Signed|0.0625|0|km/h|

Message example:
- 0xCE 8 00 00 00 00 00 00 00 00
    - V_WHL_FLH: 0km/h
    - V_WHL_FRH: 0km/h
    - V_WHL_RLH: 0km/h
    - V_WHL_RRH: 0km/h