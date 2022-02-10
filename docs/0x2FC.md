# CAN ID 0x2FC Central locking and door status:
- Type: CAN Standard
- ID: 0x2FC
- DLC: 7
- Tx method: cycle
- Cycle time: 5s

|Signal|Start bit|Length|Order|Value type|Factor|Offset|Unit|
|------|---------|------|-----|----------|------|------|----|
|DOOR_STATUS|8|8|Intel|Unsigned|1|0||
|BOOT_BONNET_STATUS|16|8|Intel|Unsigned|1|0||

- DOOR_STATUS
    - 0x1: FL door opened
    - 0x4: FF door opened
    - 0x10: RL door opened
    - 0x40: RR door opened

- BOOT_BONNET_STATUS
    - 0x1: Boot opened
    - 0x4: Bonnet opened

Message example:
- 0x2FC 7 81 00 01 FF FF FF FF
    - doors closed, boot opened